---
title: "Lubuntu 22.04 LTS won't boot after installation-newbie"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by peasant-pawn on 2022-10-20
I installed Lubuntu 22.04 from a bootable usb (my windows 8 was unbootable). However when restarted my laptop to enter the bios and change the boot order priority to select lubuntu as no. 1, Lubuntu was not an option. Only the dvd rom and usb sandisk and sandisk UEFI was available.  

I then installed boot repair and got the following report: [https://paste.ubuntu.com/p/HhxRdBXFSd/](https://paste.ubuntu.com/p/HhxRdBXFSd/) 

Please help! Been trying since monday to get my laptop back! Thanks!

---

### Post by tea for one on 2022-10-20
Line 63 - Boot-repair has detected only one OS on partition sda3.
Therefore, there was no need to change the boot order priority.

The partitions look a bit unusual.
Usually with a UEFI clean install you would have two partitions, an ESP and a System partition.
How did you arrive at 5 partitions?

If you remove the USB installer and DVD (if any), power off and then reboot?
Any luck?

---

### Post by peasant-pawn on 2022-10-21
Googled:"how to partition my hard drive when installing linux for the 1st time". Read like 5 articles then followed the common points. However 5 partitions was a mistake, it was supposed to be 4: boot-loader, swap, (/)root and /home.  

unfortunately no. A message appeared on screen saying I need to insert a device and press any key. The problem was there was no option in the bios to boot from lubuntu (for windows it would have been windows boot manager).

However, I disabled legacy boot in the bios, did a fresh install with a partition labeled efi/boot (per instruction of the install wizard) and it worked! When legacy boot was enabled, the boot partition was incorrect hence it did not boot(I think). 

Anyway, thanks for your help. I am happy and really enjoying my experience thus far. My laptop was extremely sluggish with windows 8.1. Now it runs so much smoother! I wanted to change long ago but was afraid something would go wrong. Just need to get used to the OS. Had to get the wifi driver sorted, now onto the sound driver. Cheers.

---

