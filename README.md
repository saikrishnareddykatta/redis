# Redis
Learnings about Redis

Redis is a type of NoSQL database but it is not similar to other NoSQL databases like MongoDB and it is very different from SQL databases like Postgres and MySQL.

In Redis, Data is stored in the format Key Value pair (similar to JSON Object). Unlike other databases that runs on Disk and stores all information on Disk. Redis run on our wokring memory (RAM). This means that Redis is incredibly fast but it is more volatile because if our system crashes, we are going to lose all our information unless we are backing data consistently.

Redis is not used as actual persisitemnt database store like MongoDB or Postgres and instead it is used more for cache. Example: We use Redis when we need access to things alot or things which take long time to compute. We store those kind of computations and key value pairs in redis.

Redis is going to be build on top of a traditional database. We will be having MongoDB or Postgres sitting on background and Redis sitting on the front of that database. Anytime we have long or slow query to database or we have data that we access all the time but that doesn't change that much, we are going to store that data in redis as well as in our database. When we are going to get that information if that data is already available in redis you can access that data in milliseconds as opposed to going all the way to database to computing the data and then coming all the way back which is going to take hundreds or thousands of milliseconds depending on hown complex the data is.

## Basic Commands in Redis

SET name kyle // OK

GET name // "kyle"

SET age 26

GET age // "26"

In Redis when we access data we are going to recieve data in the form of string

DEL age // (integer) 1

GET age // (nil)

EXISTS age // (integer) 0

EXISTS name // (integer) 1

KEYS * // 1) "name"

flushall // OK - it deletes everything in the database

KEYS * // (empty list or set)

SET name kyle // OK

GET name // "kyle"

## Handling Expirations in Redis

TTL name // (integer) -1 - this means that there is no expiration for key "name"

We can make keys expire after sometime

EXPIRE name 10 // (integer) 1 - expire command - name of the key - expiration time for the key

TTL name // (integer) 9

TTL name // (integer) 8

TTL name // (integer) 7

TTL name // (integer) 6

TTL name // (integer) -2

GET name // (nil)

When we want to set up an expiration while setting up the key itself

SETEX name 10 kyle //OK - SETEX command - name of the key - expiration time - value of the key

TTL name // (integer) 9

TTL name // (integer) 8

TTL name // (integer) 7

## Lists



