---
title: "Help with Dual Boot (SATA &amp; IDE)"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by MyBabeAbe on 2007-05-19
Okay – I've been trying to dual boot Ubuntu and XP for a while now and I've tried a couple different ways I've found here but everything gives me some problems so I thought I should go ahead and ask here.  I'm sure all of the things that have gone wrong are fixable, but this is my first go at linux so hopefully I can get some help.
Here is the way my drives are set up:

hda : 
Music (80GB)
hdb: 
Partition1: ext3 (20GB)
Partition2:  swap (2GB)
Partition3: Data (138GB)
sda: 
Partition1:  Windows (100GB)
Partition2:  Data (150GB)

Here's what I've tried:  
I tried just unplugging everything except the Hard drive I intend to install Ubuntu on and installing it there then connecting my other two drives after I install.  That worked except:  When I tried to mount my other two drives using ntfs-config it found the SATA drive and those worked perfectly, but it never found my Music drive.  Then I tried to run it again to see if it would find my Music drive and it gave me some error and unmounted all of my drives including the data partition on the same drive as my Ubuntu partition.  Then I restarted and ran it again – this time my Music drive showed up but none of the others did.  Windows also did not show up in GRUB using this method (but I think you can add it later by editing the menu.lst file, correct?)

I also tried just installing it with all drives connected and GRUB gave me “Error 17”

I tried installing it with everything but my windows hard drive plugged in, but GRUB gave me a missing file error.

I would appreciated any instructions you can give me on an alternate method to dual boot XP on a SATA and Ubuntu on an IDE or ways to fix any problems I've encountered.  I HAVE looked at this thread : [http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902) and have tried many of the options given in the “dualboot with a SATA and an IDE drive: “ threads.

Sorry if I should have posted this as a reply to one of those threads I didn't want to bump them.

---

