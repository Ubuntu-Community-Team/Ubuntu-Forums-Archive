---
title: "Ubunto dev not found"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by banditxkr on 2011-01-10
Hey everyone, thanks in advance for the help!

The Problem: I just installed ubunto 10.10 on my desktop and it wont boot. A cursor flashes for a few seconds and then drops to a busybox terminal. Here is the error given: 

ALERT! /dev/disk/by-uuid/46e28492-a3df-422b-a4b1-fe7f934993ab does not exist. Dropping to a shell!

the uuid is different than that above but I don't think it's relevant.

I've tried reinstalling (and installing older versions) and running fdisk and re-install grub  (no change).
I also was going to modify my fstab but when I opened it, it didn't look right to me. All it said was:
     aufs / aufs rw 0 0 
     tmpfs /tmp tmpfs nosuid,nodev 0 0
     /dev/sda4 swap swap defaults 0 0

Relevant info (maybe): system is a dual boot with windows 7. System previously had Ultimate Edition installed on it (ubuntu variant)

Here is my grub info:  
          GNU GRUB version 1.98+20100804-5ubuntu3
recordfail
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set (uuid here)
linux /boot/vmlinuz-2.6.35-22-generic root=UUID=(UUID here) ro quiet splash
initrd /boot/initrd.img-2.6.35-22-generic


Hopefully someone can help me figure this out! I miss Linux! :)

---

