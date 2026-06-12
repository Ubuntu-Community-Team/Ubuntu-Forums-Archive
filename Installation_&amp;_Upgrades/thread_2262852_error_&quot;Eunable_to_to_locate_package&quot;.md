---
title: "error &quot;E:unable to to locate package&quot;"
date: 2015-01-27
forum: Installation &amp; Upgrades
---

### Post by jared both on 2015-01-27
Running Ubuntu kernel 3.8.13.29 (armv7l) on an ODROID U3.

Using the command apt-get in the  terminal results in finding the package online but not after it downloads.

---

### Post by MAFoElffen on 2015-01-27
Of course you suing a device like that I'm assuming you know what you are doing and have root permissions right(?)

apt-get downloads package deb files to "/var/cache/apt/archives". Have a look there and see if it is there.

If not, do 
```

sudo apt-get -d package_name

```
the '-d" option is the same as "--download-only"... and will download without installing it, to that same directory. Of course you could always also just use wget to dl it to any directory...

---

### Post by jared both on 2015-01-28
i did some more research and there is a separate WINE program for arm based processors.

---

