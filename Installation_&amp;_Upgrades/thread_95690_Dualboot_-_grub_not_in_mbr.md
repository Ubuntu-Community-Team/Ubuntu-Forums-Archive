---
title: "Dualboot - grub not in mbr ?"
date: 2005-11-27
forum: Installation &amp; Upgrades
---

### Post by Aerial on 2005-11-27
Hey guys. 

I've tried reading the threads in here to find a solution, but without luck, so here it goes .
I've installed Ubuntu x64 on dualboot with XP. I installed the grub-boot loader, but when im booting i'ts going directly into XP ? - like ubuntu was never installed

Is there anything I can write to boot.ini og something to make it boot in ubuntu ?

The disk with mbr is sata, while the rest of the disks are ide. Is this a problem for the bootloader ?

Hope you can out  - thanks in advance ;)

---

### Post by bwog on 2005-11-27
Sata should work, you installed on it. Boot,ini doesnt help here.

What you can try is to restore Grub: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)

You have to put grub on the right place, suppose your sata disk is sda, you do

grub-install /dev/sda

If you cant figure it out, just come back to as here (in that case write some info on disks and partitions). Good luck.

---

### Post by Aerial on 2005-11-27
Figured it out. (sort of) 

the mbr is on the satadisk and when this is the disk I boot from it goes directly into XP. 
When i hit F8 and select the master IDE it goes into grub. 

Dont know why / how I did it , but now Ubuntu's running like a dream \\:D/

---

### Post by bwog on 2005-11-27
Great that ubuntu is working now. When you get tired of this way of booting you can always try what I said in the previous post.

---

### Post by mo_x on 2005-11-27
I had the problem with 5.04 that th MBR was written to the wrong disk. With 5.10 it writes the MBR to the correct disk (SATA) but the drive numbers in the grub config were wrong. I work around it by disconnecting the ide drive before installing Ubuntu.
I also made a bug report so it is a known issue.

---

