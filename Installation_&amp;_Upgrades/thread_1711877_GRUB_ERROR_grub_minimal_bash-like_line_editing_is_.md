---
title: "GRUB ERROR: grub minimal bash-like line editing is supported"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by smouser on 2011-03-21
Hi Guys,
Ubuntu didn't start up all of a sudden. It got error and stuck at :  Minimal BASH-like line editing - Ubuntu Forums. I tried many ways  suggested to go into menu mode but failed.
I followed online solutions.. but none of them helped. I tried to list all partitions and I got this:
ls
(memdisk), (hd0), (hd0,msdos), (fd0)
i tried 
root (hd0)/boot , it said unknown filesystem
root (hd0,msdos)/boot, but it's a windows partition
root (f0)/boot, it said read error

The setup is dual boot with wubi, so i logged on to windows7 and  installed partition magic, but i couldn't see the linux parittion, the whole harddisk is 500G, but only 2xxG is visible in NTFS

I used liveCD to boot the system, but when i run sudo fdisk -l, i didn't see anything

I have no idea why it happened, and the last successful log on was in Ubuntu, so i doubt it's due to windows update..

I am going to try Solution #1 (10.04) in wubi megathread.

Can anyone suggest what has actually gone wrong? WIll i able to recover  the data in my linux parition given partition magic cannot see it?

THanks!

WIll move this to general help, please remove/ignore this message. Sorry for inconvenience

---

