---
title: "Postgres with Ubuntu 16.04 very slow"
date: 2018-01-18
forum: Installation &amp; Upgrades
---

### Post by barmi2 on 2018-01-18
I updated from Ubuntu 14.04 to Ubuntu 16.04 and Postgres is very slow now. I have written a little script to test this behaviour:

```
import os, random, timeit, subprocess


# 007F hex (127)
# 07FF hex (2047)
# FFFF hex (65535)
# 10FFFF hex (1,114,111)
def get_random_unicode(length):
    get_char = unichr
    #include_ranges = [ (0x4e00, 0xa000), (0x3400, 0x4e00), ] # chinese chars (1000 -> 46.25/0.05 vs. 36.36/0.04)
    include_ranges = [ ( 0x16A0, 0x16F0 ) ] # celtic runes (1000 -> 40.91/10.32 vs. 33.45/0.61)
    alphabet = [ get_char(code_point) for current_range in include_ranges
        for code_point in range(current_range[0], current_range[1] + 1) ]
    return ''.join(random.choice(alphabet) for i in range(length))


def cmd(q):
    cmd = ['psql'] + ['-q'] + ['-d'] + ['testdb'] + ['-c'] + [q]
    (out,err) = subprocess.Popen(cmd,stdout=subprocess.PIPE).communicate()

start = timeit.default_timer()
(out,err) = subprocess.Popen(['dropdb', 'testdb'], stdout=subprocess.PIPE).communicate()
(out,err) = subprocess.Popen(['createdb', 'testdb'], stdout=subprocess.PIPE).communicate()
cmd('CREATE TABLE testtable (id integer NOT NULL, q character varying(255) NOT NULL);')
for i in xrange(1, 1000):
    #print i
    #searchstring = ''.join(random.choice(string.ascii_uppercase + string.digits) for _ in range(10)) # ascii
    searchstring = get_random_unicode(10).encode('utf-8') # utf-8
    cmd ("INSERT INTO testtable VALUES (" + str(i) + ", '" + searchstring+ "')")
stop = timeit.default_timer()
print stop - start

start = timeit.default_timer()
cmd('ALTER TABLE ONLY testtable ADD CONSTRAINT testtable_q_key UNIQUE (q);')
stop = timeit.default_timer()
print stop - start 

```

Postgres is more than 10 times slower when running the script with celtic runes -> UTF-8 Range 0x16A0, 0x16F0
Is anybody able to test this script on both Ubuntu 14.04 and Ubuntu 16.04. Would be interesting if you get the same result - or does anybody know what the problem could be?

THX

---

### Post by barmi2 on 2018-02-12
It's a glibc bug: After upgrading from Ubuntu 14.10 (glibc 2.19) to 15.04 (glibc 2.21), we are experiencing a big performance regression in one particular PostgreSQL index creation. The index creation now takes more than 10 minutes, while before it was done in about 30 seconds.


[https://sourceware.org/bugzilla/show_bug.cgi?id=18441](https://sourceware.org/bugzilla/show_bug.cgi?id=18441)

---

