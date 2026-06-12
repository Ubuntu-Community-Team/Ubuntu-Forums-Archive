---
title: "perl 5.10.0 installation error on ubuntu 11.04"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by ravish112 on 2011-08-27
Hi,
 
I am trying to install perl 5.10.0 from source on ubuntu 11.04 and I got following error.
 
Could someone help in this scenario
 
The error is :-
 
miniperlmain.o: [COLOR=#0000cc]In function[/COLOR] `main':
miniperlmain.o(.text+0xbf): undefined [COLOR=#0000cc]reference[/COLOR] to `pthread_mutex_destroy'
opmini.o: In function `Perl_op_free':
opmini.o(.text+0x3bb): undefined reference to `pthread_mutex_lock'
opmini.o(.text+0x3e2): undefined reference to `pthread_mutex_unlock'
opmini.o(.text+0x409): undefined reference to `pthread_mutex_unlock'
opmini.o: In function `Perl_scalar':
opmini.o(.text+0xb46): undefined reference to `pthread_getspecific'
opmini.o: In function `Perl_list':
opmini.o(.text+0x11a2): undefined reference to `pthread_getspecific'
opmini.o: In function `Perl_load_module_nocontext':
opmini.o(.text+0x5228): undefined reference to `pthread_getspecific'

Thanks,
Ravish

---

### Post by dino99 on 2011-08-27
[http://perl-begin.org/](http://perl-begin.org/)

---

