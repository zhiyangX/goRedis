# Implementation of Redis using go

## Description
- Build the middleware and Implement an Echo TCP Server 
- Implement the Redis communication protocol on top of TCP Server
- Implement a Redis Database with go high concurrency feature

## Structure

### Five layer:

1. TCP Service Layer

2. RESP Protocol layer

   REdiscover Serialization Protocol:
   
   The protocol for client and server to communicate; Using TCP connection, what type of data to send to represent redis communication.

   Five format of communication:

   - Simple Strings: start with "+", end with "\r\n", 
   
     E.g. +OK\r\n

   - Errors: start with "-", end with "\r\n"

      E.g. -Error message\r\n
   - Integers: start with ":", end with"\r\n"

      E.g. :123\r\n
   - Bulk Strings: start with"$", followed by byte number, end with "\r\n"

      E.g. $9\r\n123456789\r\n

      Empty string: $0\r\n\r\n

   - Arrays: start with "*", followed by number of element

     E.g. SET key value
     *3\r\n$3\r\nSET\r\n$3\r\nkey\r\n$5\r\nvalue\r\n

3. Database using memory

4. Database using hard disk

5. Cluster Layer


## TODO
Turn single server redis into a cluster