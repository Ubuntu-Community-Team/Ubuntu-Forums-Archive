---
title: "Dual Boot Ubuntu 10.10 and Windows 7 (Ubuntu installed first)"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Ir0nMa1deN on 2010-12-30
I'm trying to dual boot Ubuntu 10.10 and Windows 7 on my Toshiba Satellite. The hard drive is 500gb. I tried using a partitioning tool to reduce the size of my primary partition (the one where Ubuntu is currently installed) but I couldn't find a way to do it. My plan is to shrink my partition to 250 gb, which would leave 250gb of unallocated space. When I put in the Windows 7 install disk, that 250gb of unallocated space should show up and let me install Windows there. Again, I have Ubuntu 10.10 installed as the only operating system right now. I tried putting in the Windows CD and using the built in tool (in advanced options) to resize my primary partition from there but it just showed 2 partitions which Windows was not able to install to. Can anyone show me how to do this without having to redo Ubuntu? I know it would be easier to just put in the windows cd, delete all the current partitions on the harddrive, then make 2 partitions of 250gb and install Windows in one of them, and Ubuntu in the other. But again, I'd rather not have to redo Ubuntu. Especially since I'm a linux noob so even though I don't have much on here I'd rather keep it.

---

### Post by bludgard on 2010-12-30
You could boot from your Ubuntu LiveMedia and choose Try Ubuntu.Then go to System>Administration>GParted Partition Manager.

This should be able to sort your partitioning problems.

---

### Post by wilee-nilee on 2010-12-30
Post a screen shot of gparted first, you will need to boot the live Ubuntu cd to shrink Ubuntu and build a ntfs for W7 if you don't preformat the NTFS you will unallocate the Ubuntu.

---

### Post by Ir0nMa1deN on 2010-12-31
Used gparted to cut my Ubuntu partition in half, left the rest to Windows 7. Install went smoothly, within half an hour I was at my Windows 7 desktop. Too bad I forgot that my computer hates Windows 7 and wi-fi doesn't work :( So I said "screw this" and decided to try Vista. Vista couldn't get past "completing installation" so I tried again like 5 times (googled vista stuck on completing installation and tried what other people said, nothing worked) So then, with Ubuntu gone and no operating system installed, I installed Ubuntu again, using the entire hard drive. I just won't dual boot cause this is stupid. I could've gone with Windows XP but whatever it's too late now. Thanks anyway.

---

