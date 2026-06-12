---
title: "Very slow DNS in 10.04Beta1"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by wkulecz on 2010-04-02
After another 479 updates DNS lookups are still horribly slow, ~5 seconds as this terminal command shows:

 
wally@U-10:~$ date && nslookup [www.nasa.gov](www.nasa.gov) && date
Fri Apr  2 16:53:57 CDT 2010
Server:		128.157.5.23
Address:	128.157.5.23#53

Non-authoritative answer:
[www.nasa.gov](www.nasa.gov)	canonical name = [www.nasa.gov.speedera.net](www.nasa.gov.speedera.net).
[www.nasa.gov.speedera.net](www.nasa.gov.speedera.net)	canonical name = [www.nasa.gov.edgesuite.net](www.nasa.gov.edgesuite.net).
[www.nasa.gov.edgesuite.net](www.nasa.gov.edgesuite.net)	canonical name = a1718.x.akamai.net.
Name:	a1718.x.akamai.net
Address: 208.22.87.113
Name:	a1718.x.akamai.net
Address: 208.22.87.90

Fri Apr  2 16:54:02 CDT 2010
wally@U-10:~$



Doing the same on 8.04 (its a dual boot setup) results in times less than 1 second.  Other nameservers, including opendns.com (208.69.38.150) are the same, ~5 seconds.

This makes interactive website usage, like this forum, painful.

I've removed the libnss-mdns package as suggested in this thread:
[http://ubuntuforums.org/showthread.php?p=9049155](http://ubuntuforums.org/showthread.php?p=9049155) and it had little to no effect after rebooting.


I had hope this round of updates might fix the issue.


Non-interactive usage like:

     sudo aptitude safe-upgrade 

is fine since you are not sitting there waiting for the DNS to respond.

---

### Post by Aenima99x on 2010-04-02
That's not 5 seconds, it's .05 of a second. 
I'm getting immediate responses every time I do the lookup, so maybe it's your DNS provider. But .05 of a second is really nothing.

```
Fri Apr  2 16:24:36 PDT 2010
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
www.nasa.gov	canonical name = www.nasa.gov.speedera.net.
www.nasa.gov.speedera.net	canonical name = www.nasa.gov.edgesuite.net.
www.nasa.gov.edgesuite.net	canonical name = a1718.x.akamai.net.
Name:	a1718.x.akamai.net
Address: 72.246.103.43
Name:	a1718.x.akamai.net
Address: 72.246.103.88

Fri Apr  2 16:24:36 PDT 2010

```

---

### Post by LADmaticCA on 2010-04-02
I too am experiencing slow dns lookups on my laptop. I started a thread [here.]("http://ubuntuforums.org/showthread.php?t=1441818")

---

### Post by wkulecz on 2010-04-13
> That's not 5 seconds, it's .05 of a second. 

Math impaired?

Date command returns HR:MIN:SEC time format.  Turst me it seems longer than 5 seconds when you are staring at the screen!

---

