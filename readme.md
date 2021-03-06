# Specie [![Build Status](https://travis-ci.org/uitgewis/specie.svg?branch=master)](https://travis-ci.org/uitgewis/specie) [![Code Climate](https://codeclimate.com/github/uitgewis/specie/badges/gpa.svg)](https://codeclimate.com/github/uitgewis/specie)


Specie is an API for exchanging currencies.

> **NOTE** This is not a real thing. 

## Requirements

* PHP (>= 5.6)
* MySQL (>= 5.6)
* nginx (>= 1.10)
* Redis (>= 3.2)
* Debian (= 8.x)
* sendmail

## Installation
```bash
# Clone the repository
$> git clone https://github.com/uitgewis/specie.git 

# Install application dependencies
$> cd specie && composer install --prefer-dist && cd -  

# Configure environment
$> cp specie/.env.example specie/.env; vim specie/.env

# Create database
$> mysql -uroot -e 'create database specie;'

# Run database seed and migrations
$> php specie/artisan migrate

# Add a hostname alias
$> sudo echo -e"127.0.1.1\tspecie.dev" >> /etc/hosts        

# Edit, link and reload
$> vim specie/etc/specie.dev && \
   cp specie/etc/specie.dev /etc/nginx/sites-enabled && \
   systemctl reload nginx

# Win! 🎉 Have a beer 🍻
$> curl -s http://specie.dev
{"status":"ok","version":"Lumen (5.2.7) (Laravel Components 5.2.*)"}
```

## API Overview

**Note: All currency valuations are relative to the South African Rand (ZAR).**

Uri               |  Verb | Description 
:---------------- | :---: | :-------------------------------------
/                 |  GET  | Status and version information
/currency/{code?}  |  GET  | Currency valuations
/exchange         |  POST | Exchange currency

**Suppoted Currencies**
* US Dollars (USD)
* British Pound (GBP)
* Euro (EUR)
* Kenyan Shilling (KES)

## Tests
Tests can be run through PHPUnit :tada: :tada: :tada:
```bash
$> phpunit tests/
```
