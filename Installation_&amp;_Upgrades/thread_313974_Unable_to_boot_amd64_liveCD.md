---
title: "Unable to boot amd64 liveCD"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by blaznlion on 2006-12-06
I am new to ubuntu and tried to boot up the AMD64 LiveCD to install ubuntu on my PC.  Everytime I try to boot the LiveCD, it keeps crashing when trying to detect my Seagate 300GB SATA hard drive.  My motherboard is a soltek k8tpro-939 and has the latest BIOS.  I have also tried to install Gentoo to see if it had the same problem and it does.  I've tried disabling the VIA onboard SATA controller and that did not fix it.  The board uses the Promise SATA controller as the default and the VIA for Raid which is not used.  I've search through the forums but did not find anything that resembles my problem.

Can anyone point me in the right direction?  I really would rather not put in an IDE Hard Drive to solve this.

---

### Post by ReaderRat on 2006-12-06
I had a similar problem, and I solved it by changing my SATA drives to act as IDE drives (in the BIOS). I do not use RAID.

---

