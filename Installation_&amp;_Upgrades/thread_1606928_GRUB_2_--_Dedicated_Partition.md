---
title: "GRUB 2 -- Dedicated Partition"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by vikrang on 2010-10-27
I was going through Mr Steve  (GRUB -legacy )and Herman's posts on installing GRUB in a separate partition..The article by Mr Steve is slightly old but nevertheless also applies to GRUB2.
 
[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)
 
In a nutshell, Mr Steve asks to do the foll to make GRUB independent of OS
 
1. Create a separate partition of 1 MB size
2. Copy Stage 1, Stage 2 and menu.lst from an existing distro without Kernel
3. Reference GRUB partition to MBR 
 
My doubts are 
 
Currently I have Win 7 boot loader in my MBR
 
1.Assume I create the GRUB partition as "logical partition" and link it to MBR as mentioned above. Now , suppose I accidentally delete the 1MB partition, on reboot will my Win 7 bootloader take over or I will get boot errors whereby I have to scratch around for my win 7 install disk and re-install Win 7 Loader to Bootsector? (I want to avoid this hassle!!)..I presume that by making a dedicated GRUB partition my Windows config will remain untouched..meaning by the above method , it is only temporarily delinked
 
2. The big Qn , What files I have to copy for GRUB 2 ...Right now there are 3 places where the files are stored./boot/grub , grub.cfg and /etc/default where other files like 40_custom ,10_xxxx, 20_xxxx,30_osprober  so on and so forth is also stored.
 
3. Can LILO be booted from GRUB2? (planning to install Slack / Zenwalk)

---

### Post by vikrang on 2010-10-27
I got the amswer by searching Herman's threads
 
[http://ubuntuforums.org/showthread.php?t=1585598](http://ubuntuforums.org/showthread.php?t=1585598)
 
:P

---

