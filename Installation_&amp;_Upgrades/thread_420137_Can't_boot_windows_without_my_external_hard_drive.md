---
title: "Can't boot windows without my external hard drive"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by severinrubio on 2007-04-23
Hi,

I recently decided to install ubuntu on my laptop, but becuse of a lack of space, I installed it on my external drive. Everything worked, XP or ubuntu, untill I tried to restart my computer without my external hard drive...

In fact, I can no longer boot on XP without my external drive :confused: 


Can someone help me ?

Bye

---

### Post by confused57 on 2007-04-23
> **severinrubio said:**
> Hi,

I recently decided to install ubuntu on my laptop, but becuse of a lack of space, I installed it on my external drive. Everything worked, XP or ubuntu, untill I tried to restart my computer without my external hard drive...

In fact, I can no longer boot on XP without my external drive :confused: 


Can someone help me ?

Bye

What happened is that you installed grub to your internal hard drive mbr, you'll need to restore your Window's IPL code in order to be able to boot Windows without the external drive connected:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

You can use also use the Super Grub Disk to repair your mbr, as well as boot Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

