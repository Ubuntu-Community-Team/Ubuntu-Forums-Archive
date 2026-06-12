---
title: "Perl - Dynaloader issue"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by jojomeuh on 2013-02-03
Hi,

I hope it the better (less worse) place to post it.

I got that:

```
root@overo:~/media_build# ./build
/usr/bin/perl: symbol lookup error: /usr/bin/perl: undefined symbol: boot_DynaLoader

```
ok...

... ok

I've to present myself:

```
root@overo:~/media_build# cat  /proc/version
Linux version 2.6.34 (neil@cumulus) (gcc version 4.3.3 (GCC) ) #1 Mon Feb 21 11:17:21 PST 2011
```

build is a script to prepare "make" operation.

My point is to install that patch in order for a "caspa" camera to work on a "gumstix" board. I don't have neither apt-get nor git. 

I understand the problem mere a perl problem than somewhat else so that it doesn't really matter what is in this build script but anyway it's there:

[http://git.linuxtv.org/media_build.git](http://git.linuxtv.org/media_build.git)


edit: abit more details

the make command gives:

```
root@overo:~/media_build# make
make -C /home/root/media_build/v4l 
make[1]: Entering directory `/home/root/media_build/v4l'
scripts/make_makefile.pl
/usr/bin/perl: symbol lookup error: /usr/bin/perl: undefined symbol: boot_DynaLoader
Updating/Creating .config
make[2]: Entering directory `/home/root/media_build/linux'
/usr/bin/perl: symbol lookup error: /usr/bin/perl: undefined symbol: boot_DynaLoader
**Version 2.6.34 not supported**
/bin/sh: exit: line 30: Illegal number: -1
make[2]: *** [apply_patches] Error 2
make[2]: Leaving directory `/home/root/media_build/linux'
/usr/bin/perl: symbol lookup error: /usr/bin/perl: undefined symbol: boot_DynaLoader
make[1]: *** No rule to make target `.config', needed by `.myconfig'.  Stop.
make[1]: Leaving directory `/home/root/media_build/v4l'
make: *** [all] Error 2

```

---

