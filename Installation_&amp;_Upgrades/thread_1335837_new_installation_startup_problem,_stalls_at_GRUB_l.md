---
title: "new installation startup problem, stalls at GRUB loading"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by ahunter10 on 2009-11-23
I am having problems with my new 9.10 installation.  During startup I get to the GRUB loading message and then nothing else happens.  It will stall there forever.

Info about my system:
-250GB IDE HDD contains root partition, swap partition, and an empty FAT32 partition (eventually for windows maybe)
-500GB SATA HDD contains /home partition.  
-ACHI mode enabled in BIOS. OS sees both disks as SATA
-500GB disk is sda, 250GB disk is sdb
-64 bit kernel

Interesting observations:
When I select the 250GB disk (which contains root partition) as the startup disk, I never get to the GRUB loading message. Startup stalls at "Verifying DMI Pool DATA ..........", which is interesting because the 250GB disk should be the startup disk. I only see the GRUB loading message when I select the 500GB (/home) disk as the startup disk.

Initially it started up fine.  A couple restarts later I got to the Ubuntu splash screen, but I got a error about how it couldn't find the disk with UUID=<some UUID>.  It went through a long process of repairing the disk (or something like that).  I think I started up at lease once since then, but now I never reach splash screen. 


Anybody have any ideas?  I booted with the live CD just fine.  I could see both hard drives.  the fstab file looks fine, but I really don't know very much so maybe there is something wrong with it?  

Could it be an incorrect BIOS setting?  Did I partition wrong?  Hopefully there is a solution that doesn't involve reformatting the disks, i've already put some time into setting things up. Any help is much appreciated.

---

### Post by ahunter10 on 2009-11-23
UPDATE:  I just let the computer hang at the GRUB loading message for the longest I have yet (nearly 30 minutes). All of a sudden the Ubuntu splash screen appears and the OS starts up like normal.  

This is a good thing, but does anybody know why it is taking so long for GRUB to start the OS?  I'd rather the computer didn't take a half hour to start up every time.  Again, any help/ideas are much appreciated.

---

### Post by namok on 2009-11-24
[This may be helpful.]("http://ubuntuforums.org/showthread.php?p=8234882")

---

