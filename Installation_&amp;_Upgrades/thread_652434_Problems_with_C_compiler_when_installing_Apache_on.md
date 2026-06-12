---
title: "Problems with C compiler when installing Apache on my linux ubuntu 7.10"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by malola123 on 2007-12-28
hi, 

I just downloaded the apache package and tarred it to my /usr/src directory.


I entered the command:   ./configure --enable-so --with-mpm=worker

to start the installation.

However, I get the following error:


[B]root@Sriram:/usr/src/httpd-2.2.6# ./configure --enable-so --with-mpm=worker
checking for chosen layout... Apache
checking for working mkdir -p... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1

Configuring Apache Portable Runtime library ...

checking for APR... reconfig
configuring package in srclib/apr now
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
Configuring APR library
Platform: i686-pc-linux-gnulibc1
checking for working mkdir -p... yes
APR Version: 1.2.11
checking for chosen layout... apr
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
configure failed for srclib/apr

[/B]



I checked the config.log file but could not make anything out of it.

PLZ help!!

Thanks!

---

### Post by taurus on 2007-12-28
You need to install the build-essential package first before you can build anything from source.

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Pumalite on 2007-12-28
Do you have build-essential installed?
sudo aptitude install build-essential

---

### Post by malola123 on 2007-12-28
Thanks for the help guys!!  works like a charm!

---

