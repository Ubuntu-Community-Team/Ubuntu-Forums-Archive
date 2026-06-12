---
title: "Bootloader not installing"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by xfceslacker on 2006-09-26
Ok... I have two hard drives. The master has two ext3 partitions and a swap. The slave has Windows XP installed on it. I deleted everything on the Linux drive(the master) and made the 3 partitions. I then installed Gentoo Linux on one of them. Everything went fine except the bootloader didn't install right. I just got a blank screen when I restarted. So then I stuck in my Windows CD and hit FDISK /MBR to get something back because I needed the computer. Now I just tried to install Ubuntu on the Linux drive. Everything went fine. In the install it had all my OSes listed when it installed the bootloader. The problem is that it didn't overwrite the windows bootloader... Is there anyone who can help me out? The Ubuntu community has always been very helpful

Thanks,
xfceslacker

---

### Post by Gotterdammerung on 2006-09-26
you must install the bootloader in MBR of /dev/hda (or of /dev/sda) to make it overwrite windows's bootloader.

---

