---
title: "Gutsy wont boot Error 15 file not found"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by pstavs on 2007-11-16
Hi All,

I am a relative Linux noobie, but have used Ubuntu for a little over a year now. I have booted from the live cd to get my laptop back up (hp compaq nx9420) running kubuntu 7.10 Gutsy. It seems in the past few days some updates came down, and now I can't boot... I am guessing its related to these updates anyhow. 

This morning I burned a CD and when I removed it I got an error "unable to unmount device blah blah blah do it manually" I probably should have done it there and then but being the laziest guy in the world I just ignored it. After a restart though I am unable to boot so here I am, wandering what I have done to upset Ubuntu. HELP!!! I need this sorted asap. I am not sure how to get to and mount my filesystem or at least the boot partition to fix it.

I am anxiously awaiting some response!
Peter

---

### Post by bulldog on 2007-11-16
15 : File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

Please boot the live cd and open a terminal,type ```
sudo fdisk -l
``` and copy the output to the forum.

---

### Post by Eicca on 2007-11-16
I used the "supergrub disk" to recover the grub.

---

