# trade-engine-pub [![Build Status](https://travis-ci.org/sligokid/trade-engine-pub.svg?branch=develop)](https://travis-ci.org/sligokid/trade-engine-pub)
Spring Boot microservice processing trades &amp; exposing Streaming Servlet endpoint (2016)

## Table of Contents

- [Introduction](#introduction)
  - [Overview](#overview)
  - [Architecture](#architecture)
  - [Verbs](#verbs)
  - [URI](#uri)
  - [Demo](#demo)
  - [Install](#install)


## Introduction

This Document outlines the web service provided to enable the processing of trades within the trade-engine.
The trade engine is a fiticious implementation of a currency exchange platform.
Trades submitted via the public API [https://github.com/sligokid/trade-engine-api/] are processed here and streamed via a Servlet endpoint.
No Authentication is requred by the client to access to this service.
This service is intended to be internal and function as a component in a microservice architecture

## Overview

This API uses the "Server Sent Events" (SSE) architectural style. 

## Architecture

![pub-diagram 1](https://cloud.githubusercontent.com/assets/6519496/17114623/a42dee4e-52a7-11e6-911d-d51e96fde710.png)

## Verbs

*HTTP Methods* or *Verbs* are the actions which can be used on each endpoint. There is 1 verbs supported by this API:

- **GET** - Start the processing of a trade and stream the result.

##### GET

A **GET** request returns the Event Stream representation of the next avaialable enriched trade.
This resource is intended for internal consumption via the https://github.com/sligokid/trade-engine-web component

## URI

The following table summarises all the available resource URIs, and the effect of each verb on them. Each of them is relative to the base URI for this API: `http://ec2-52-16-13-114.eu-west-1.compute.amazonaws.com:8102`.

| Resource                                              | GET                                                 | POST                                  | PUT                               | DELETE                                      |
| ----------------------------------------------------- | --------------------------------------------------- | ------------------------------------- | --------------------------------- | ------------------------------------------- |
| [/pub/tradestream]                                    | Streams the next available processed trade          | N/A                                   | N/A                               | N/A                                         |


##Demo

<img width="337" alt="preview-pub" src="https://cloud.githubusercontent.com/assets/6519496/17110830/bf0a187a-5296-11e6-8d23-a2aee0b55a66.png">

http://ec2-52-16-13-114.eu-west-1.compute.amazonaws.com:8101/pub/tradestream

#Install

``` bash
   $ git clone https://github.com/sligokid/trade-engine-pub.git
   $ cd trade-engine-pub
   $ mvn clean package
   $ mvn spring-boot:run
```
