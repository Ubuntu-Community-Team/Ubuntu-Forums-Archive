---
title: "warvox installation error"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by acidking on 2011-02-12
hello, i am trying to install [warvox]("http://warvox.org/install.html"), but ran into this error:

```

sami@sami-MacBookPro:~/warvox-1.0.1$ make
make -C src/iaxrecord/
make[1]: Entering directory `/home/sami/warvox-1.0.1/src/iaxrecord'
gcc -Wall -o iaxrecord iaxrecord.c -liaxclient
iaxrecord.c:24: fatal error: iaxclient.h: No such file or directory
compilation terminated.
make[1]: *** [all] Error 1
make[1]: Leaving directory `/home/sami/warvox-1.0.1/src/iaxrecord'
make: *** [iaxrecord] Error 2

```any idea what's it about? I've installed the dependencies as here:
```
$ sudo apt-get install build-essential _libiaxclient-dev_ sox lame ruby  ruby-dev rake rubygems libopenssl-ruby libreadline-ruby libsqlite3-ruby  gnuplot 
```^ the underlined was throwing an error, so i omitted it and installed  without, then tried to reinstall it on it's own and got this error:
```
sami@sami-MacBookPro:~$ sudo apt-get install libiaxclient-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libiaxclient-dev

```Thanks.

---

### Post by acidking on 2011-02-12
ok it's sorted, i installed* libiaxclient1_2.0.2-3build1_i386.deb* and then went back and installed* libiaxclient-dev_2.0.2-3build1_i386.deb* 


:popcorn:

---

