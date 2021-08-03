Q. Building a rate limiter using redis. Ex : Limiting user calls to 10 requests per min

Sol.

Using Redis List for each user.
Key - userId
now() - current time

times = LLEN userId
if times < 10
    LPUSH userId now()
else
    time = LINDEX userId -1
    if now() - time <= 60
        print "Exceeded the limit"
    else
        RPOP counter
        LPUSH userId now()