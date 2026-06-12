---
title: "Ubuntu 12.04 and 12.10 both boot in busybox after installing via windows 7"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by Jefferson1 on 2012-12-09
hello,

yesterday i installed ubuntu on windows 7 using wubi (both 64bit). trying to boot ubuntu it first says 
> 
try (hd0 0) ntfs5: no wubldir
try (hd0 1) ntfs5:


and then after a while busy box starts with following error message:

> Gave up waiting for root device. Common Problems:
  - boot args (cat /proc/cmdline)
   -check rootdelay= (did the system wait long enough?)
   -check root= (did the system wait for the right device?)
  - missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/B2B42B58842B1E7B does not exist. dropping to a shell!

this happens with 12.04, i also tried 12.10 but then it just starts busybox without saying anything.
also I use windows and ubuntu on the same partition; if thats neccesary.

thanks in advance
jefferson

---

### Post by darkod on 2012-12-09
In general, I don't recommend wubi at all. You should install ubuntu on its own partition, the way any OS is designed to work.

The only thing that I can think of, is that in win7 you have to start the wubi.exe with right-click, Run as Administrator. If you start it with double click, it might not have enough permissions to prepare the vitrual boot. Maybe that's where it gets stuck.

---

### Post by verzx on 2012-12-09
Yeah i've never had a problem with installing it via USB or Disc but when I seem to install it with wubi there is always a problem with it.

Install with disc or USB and it should be fine. :)

---

### Post by Jefferson1 on 2012-12-09
> **darkod said:**
> In general, I don't recommend wubi at all. You should install ubuntu on its own partition, the way any OS is designed to work.

The only thing that I can think of, is that in win7 you have to start the wubi.exe with right-click, Run as Administrator. If you start it with double click, it might not have enough permissions to prepare the vitrual boot. Maybe that's where it gets stuck.

thanks, but this didn't help.

i deinstalled ubuntu and tried to install it the normal way, what led me to another problem and maybe the coreproblem: 

i started the livecd to install ubuntu, but it said there is no diskspace avaivable, so i made a gparted cd but this didn't recognize any drive. i made a new thread about this topic because this is another problem: [Neither Ubuntu liveCD nor Gparted Disk recognize my harddisk]("http://ubuntuforums.org/showthread.php?p=12396719#post12396719")

---

