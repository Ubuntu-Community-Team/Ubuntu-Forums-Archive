---
title: "Grub 2  -Cool??"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by jfaberna on 2010-08-16
Just thought I'd report something that happened unexpectedly on Ubuntu 10.4 and Grub 2 that I thought was cool because it solved a problem before I had it.

I had a need to install both Ubuntu 10.4 and Fedora 13 on the same PC on 2 separate hard drives. I installed Ubuntu 10.4 1st on /dev/sda and then without updating 10.4, I installed F13 on /dev/sdb. While answering the question on where to install the F13 bootloader, my only choice was /dev/sdb. I was hoping that F13 would integrate the grubs on /dev/sda. 

So I thought that I either had to manually edit the grub on Ubuntu or continue to use the Func+10 button on boot to change the boot drive. 

Well when I rebooted into Ubuntu and did the Software Update, it reran update-grub and magically, grub on /dev/sda now had listed Ubuntu 10.4 and Fedora 13.

Solved my problem of editing manually, before I had to. :D

So when I needed to add a boot parameter to F13 on /dev/sdb, I just have to boot Ubuntu and rerun update-grub and I'm done.

Thanks, to those who solved this problem by creating Grub 2.

Jim A

---

