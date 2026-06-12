---
title: "get error when try to upgrade after remove desktop-base"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by emjey on 2010-01-15
heloo guys

i get this error :(

root:/boot# **apt-get upgrade **

```


Setting up desktop-base (5.0.3) ...
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/bzImage
/etc/grub.d/01_OVHkernel: line 37: syntax error: unexpected end of file
dpkg: error processing desktop-base (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 desktop-base
E: Sub-process /usr/bin/dpkg returned an error code (1)


```don't get any good solution

---

### Post by Dayofswords on 2010-01-15
looks like you needed that desktop-base

(doesnt that name kinda sound important too)

---

### Post by emjey on 2010-01-15
what i must to do?

try to re-install desktop-base
but problem still exist

---

### Post by emjey on 2010-01-15
Problem Solved

install grub :D

---

