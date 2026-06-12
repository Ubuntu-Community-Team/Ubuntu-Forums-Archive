---
title: "Package names on Ubuntu vs Redhat"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by oblivian on 2008-11-06
Hello,

I am trying to install Merak mail server on Ubuntu server 8.04-1. The problem is that Merak is certified for RH5/4 so installing Merak on Ubuntu needs a little extra effort to work. I am trying to install the following libraries and dependencies, but the naming convention seems a bit different on Redhat than that of Ubuntu. Can someone please enlighten me on how I find the equivalent packages on Ubuntu? Where do I start?

> System requirements
-------------------
 
CPU             - PC 486
Memory          - 64MB RAM

Linux kernel 2.4.x and higher
glibc library 2.2.x and higher

pthread library
pcre library
zlib library
iconv library
gd library
ldap library
openssl library
sqlite3 library
pspell+aspell library
mysql 4.1+

No other modules are required to be installed.

Please advice,

Obi

---

### Post by 4leite on 2008-11-06
are you comfortable with the command line?
if so,
```
apt-cache search 'package name'
```
for instance
```
apt-cache search pthread library
```
returns:
```
glibc-doc - GNU C Library: Documentation
libilmbase6 - several utility libraries from ILM used by OpenEXR
libpthread-stubs0 - pthread stubs not provided by native libc
libpthread-stubs0-dev - pthread stubs not provided by native libc, development files
tau - Tuning and Analysis Utilities - base profiling toolkit

```

From this example you'd want 'libpthread-stubs0' 
If you are compiling code, you'll also need 'libpthread-stubs0-dev'

You could also go system->administration->synaptic package manager
Then click on the search button...


Hope this helps.

---

