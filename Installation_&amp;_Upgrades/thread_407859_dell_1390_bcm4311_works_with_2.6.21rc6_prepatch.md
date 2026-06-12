---
title: "dell 1390 bcm4311 works with 2.6.21rc6 prepatch"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by nanog on 2007-04-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/92088](https://bugs.launchpad.net/ubuntu/+source/bcm43xx-fwcutter/+bug/92088) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I got tired of the ~30kb/s max wireless speed using the native bcm43xx driver in fesity. Based on posts in the berlios mailing list (bcm43xx developers) I decided to compile 2.6.21. The dell 1390 mini card is stable and the speed issue is fixed. I assume that this will also work in Edgy but I've upgraded everything to feisty.

I used the following guide and the default .config:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)


All the usual disclaimers about how you can really hose your system. 

Apparently 2.6.22 has additional improvements but I'm sticking to release candidates.

---

### Post by nanog on 2007-04-23
A link to the patches:

[ftp://lwfinger.dynalias.org/patches](ftp://lwfinger.dynalias.org/patches)

---

### Post by marsm on 2007-04-24
This is good news, many thanks for mentioning it!

---

### Post by keep on 2007-04-30
Hi! how do you manage to get tne new Kernel work on inspiron 1501? I have followed the link you add with the config file from /boot/config-2.6.20-15-generic. The new kernel wont to boot on my dell but boot on my Desktop. 
I have tried with both kernel 2.6.21-rc7 and 2.6.21

---

### Post by nanog on 2007-06-03
It really should work with a dell 1501. My advice is to go through .config item by item.

---

