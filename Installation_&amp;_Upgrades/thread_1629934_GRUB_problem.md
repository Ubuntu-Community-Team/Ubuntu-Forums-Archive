---
title: "GRUB problem"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by Destructo930 on 2010-11-24
So I installed Ubuntu 10.10 netbook on my Lenovo 3000 G530 and loved it. But i decided I wanted to wipe my laptop clean with a fresh install of Windows and then reinstall Ubuntu both with even partitions. So I went through and deleted and formatted the Ubuntu partition but I didnt know that in doing so I screwed myself in the fact that the GRUB would still try and load Ubuntu. So now Im stuck with it trying to load then I get an error saying "invaild filesystem. grub rescue" and Ive gone through the documentation and found nothing that helps me with the problem. I hunted to see if anyone less had this problem as well. Some did but for them reinstalling Ubuntu solved it, but I tried and it starts the install then gets to another error that is something like "initistart" or something and the install stops there. So I was wondering if anyone had any ideas on what I could do next to taking it in to a pro to have it fixed. And also I was curious if replacing the HDD would solve it, but I think the GRUB is more of a BIOS setting, correct? Thanks in advance for your help.
 
Edit: Also I should have mentioned that Im running Win7.

---

### Post by oldfred on 2010-11-24
Grub is in the MBR and controls booting. When you deleted Ubuntu the rest of grub is not there for the grub in the MBR to find. 

You can reinstall Ubuntu and that will fix it. If you are reinstalling windows that will fix it anyway as windows gives you no choice on installing the boot loader and you have to reinstall grub after a windows install anyway (if you still have Ubuntu)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by Destructo930 on 2010-11-25
Thanks oldfred. The booting/installing from grub rescue was just what I needed :P

---

