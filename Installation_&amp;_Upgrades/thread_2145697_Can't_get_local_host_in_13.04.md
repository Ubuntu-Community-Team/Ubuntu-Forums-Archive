---
title: "Can't get local host in 13.04"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by hg21 on 2013-05-16
After upgrade to 13.04 neither Firefox or Chromium browsers will access localhost.  Chromium says "Chromium's connection attempt to localhost was rejected".

This is not a problem when I go back to 12.10.

It may be a 64bit specific problem 'cos it happens on my desktop (64-bit installation) but not on a laptop (32-bit).

The contents of /etc/hosts,host.conf,hostname,hosts.allow,hosts.deny are the same in my 12.10 & 13.04

---

### Post by dentaku65 on 2013-05-17
What resides on localhost? I mean do you have some application that use [http://localhost](http://localhost) ?

---

### Post by hg21 on 2013-05-17
> **dentaku65 said:**
> What resides on localhost? I mean do you have some application that use [http://localhost](http://localhost) ?


I wanted to get to localhost:631 to deal with a printer problem.

---

### Post by fdrake on 2013-05-17
you are trying to use the cups conf feature try in the browser the address with the right port:

"localhost:231"

to check if cups is installed: ```
dpkg -s cups
```

---

### Post by hg21 on 2013-05-17
> **fdrake said:**
> you are trying to use the cups conf feature try in the browser the address with the right port:

"localhost:231"

That gives the same result, I cannot access localhost. When did it change from 631?  I've used that for years and on my laptop 631 gives cups info.

to check if cups is installed: ```
dpkg -s cups
```

dpkg -s cups
Package: cups
Status: install ok installed

---

### Post by dino99 on 2013-05-17
if you only have that printer connection issue (but no network trouble), then check the users & groups properties

---

### Post by hg21 on 2013-05-18
Solved it!

The problem was in cupsd.conf.

The line 

Listen /var/run/cups/cups.sock

was repeated twice

I replaced one of these with

Listen localhost:631

I presume this is a bug in the 64bit version of 13.04

---

