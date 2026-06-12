---
title: "Xubuntu Clean Install w/RAID 1 - Dropping to a shell!"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by cranial.nook on 2011-03-07
Hi there - I'm incredibly new to Linux, so this problem might be easy to solve, but I've searched long and far and still have not found a solution yet.

So let me start off by telling you my goal.
I am making a home file and FTP server, so I have decided to convert my old windows computer into a Linux box that can handle these tasks nicely.  I currently have two 2 TB SATA hard drives which I am wanting to use in a RAID 1 array.

My setup
Asus P5GD1-Pro with a RAID controller built into the chipset
Intel Pentium 4 Processor
2x 2 TB SATA HDD
I have a RAID 1 array enabled in my BIOS/Chipset settings which passes on POST

What I have done so far...
I have tried installing Xubuntu 10.10, Xubuntu 10.10 alternate, and Debian 6.0.0.  With the Xubuntu 10.10 alternate version, I initiated RAID and tried installing with LVM and without... With the regular version of Xubuntu I just tried installing with one big partition and I keep getting the same result.

```
Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/fb52xxxxxxxxxxxxxx does not exist.
Dropping to a shell!


BusyBox v1.15.3 (Ubuntu 1:11.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) sudo
/bin/sh: sudo: not found
(initramfs) apt-get install update
/bin/sh: apt-get: not found
(initramfs) fdisk -l
/bin/sh: fdisk: not found
(initramfs) cd /etc
(initramfs)ls
modprobe.d     default     udev     console-setup     mtab
```I'm pretty sure this has something to do with me having a RAID setup because when I unplug one of my hard drives I can get into Xubuntu CLI and login that way; however, I don't get the XFCE desktop like I should though.  When both HDD are plugged in I've tried following several other posts in this forum, but I can't do a lot of things.  For instance, sudo, apt-get, fdisk, and nano don't work and I am also missing files other people have mentioned that I could edit.

Any insight on how I might be able to make this work would be great and keep in mind I have only been using Linux for a week now, so any advice will probably have to be dumbed down a fair bit.

Thanks in advance!

---

