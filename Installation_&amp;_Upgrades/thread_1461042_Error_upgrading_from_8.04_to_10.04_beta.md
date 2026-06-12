---
title: "Error upgrading from 8.04 to 10.04 beta"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by megahost on 2010-04-23
Alright, I have downloaded the upgrade for 10.04 and installed upgraded from my previous 8.04. Everything was working all fine until I had to reboot my pc. When I did i got some errors

Mount: Mounting none on /dev

It goes on to tell me that my UUID does not exist. Then it says

ALERT! Alert! /dev/disk/by-uuid/xxxxxxxx-xxxx-xxxx-xx$ does not exist.  Dropping to a shell!

It then drops to a very simple shell which has no flexibility and is very frustrating. Help is VERY appreciated, and I'd hate to to a reformat.

EDIT:

This is the full error message

Mount: Mounting none on /dev
boot args cat /proc/cmdline
check rootdelay =(did the system wait long enough?)
check root =(did the system wait for the right device?)
missing modules ( cat /proc/modules)
ALERT! /dev/mapper/debian-root does not exist
dropping to a shell.

---

### Post by megahost on 2010-04-23
I originally thought it was apart of the UUID not existing, but it is there. Help is much appreciated

---

### Post by megahost on 2010-04-23
I looked around a little, and sources say since I am upgrading from a much earlier version, the kernel is messed up. PLEASE HELP

---

### Post by nss0000 on 2010-04-23
Well that's a real horror. Who needs that obscure baloney? I've got a many-years-old 8.04 LTS install ... bulletproof functions ... and you've convinced me **not** to try the risky upgrade to 10.04.

---

### Post by megahost on 2010-04-23
Yeah, it is ridiculous, but I remember one of the developers saying that I need the new kernel, which is also confusing. I'm sure there is a fix, but I really need some serious help lol

---

### Post by rjcroy on 2010-04-24
You might want to look at the following thread:
[http://ubuntuforums.org/showthread.php?t=1454385](http://ubuntuforums.org/showthread.php?t=1454385)
The problem could be the same.

---

