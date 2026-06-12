---
title: "Upgrade Multi Operating Systems to Ubuntu"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by texasjim37 on 2009-11-21
Hi,
First time user here.  I have a dual operating system with Windows XP and PCLinuxOS and I want to know if I can keep everything in place and only upgrade from PCLinuxOS to Ubuntu?

I am using the latest version of Ubuntu on a CD iso and everything seems to work on the Linux side but no Windows available.

If anyone can point me in the right direction I would appreciate any assistance.

Thank you all in advance.

Jim

P.S.  I am really impressed with Ubuntu .... it seems to be way ahead of PCLinuxOS.
:D

---

### Post by lmarmisa on 2009-11-21
First of all, welcome to the Ubuntu forums.

I don't see any problem in order to substitute PCLinuxOS with Ubuntu.

Simply you have to create a new installation of Ubuntu selecting manually the partition(s) where PCLinuxOS is now located.

You should define at least two partitions for Ubuntu: a small partition (about 1 or 1.5 times the size of your RAM memory) for swap; a big partition for the / directory of Ubuntu.

Ubuntu will install a dual grub loader for Windows and Linux during the installation process.

---

