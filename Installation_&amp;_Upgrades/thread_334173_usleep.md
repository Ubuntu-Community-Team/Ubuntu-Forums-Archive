---
title: "usleep"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by k3nz0 on 2007-01-08
Any knows how to install usleep in Dapper?
I can see that it has sleep but not usleep and doing a search for it doesn't come back with anything.  Any ideas?
thanks.

---

### Post by k3nz0 on 2007-01-10
never mind, it took me for ever but I found the source for it and compiled it.

---

### Post by fakie_flip on 2007-05-10
Do you mind sharing how you did that? I have usleep source code here, but when I try to compile it, it doesn't compile.

chris@ubuntu:~/Desktop$ gcc usleep.c -o usleep
usleep.c: In function &#8216;usleep&#8217;:
usleep.c:11: error: &#8216;NULL&#8217; undeclared (first use in this function)
usleep.c:11: error: (Each undeclared identifier is reported only once
usleep.c:11: error: for each function it appears in.)
chris@ubuntu:~/Desktop$ cat usleep.c 

#include <sys/types.h>
#include <sys/time.h>


void usleep(x) {
        struct timeval  time;

        time.tv_sec= x/1000000;
        time.tv_usec=x%1000000;
        select(0, NULL, NULL, NULL, &time);
        }

chris@ubuntu:~/Desktop$

---

