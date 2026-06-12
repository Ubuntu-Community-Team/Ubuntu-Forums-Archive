---
title: "[SOLVED] space needed for upgrade"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by caro on 2008-10-22
I'm trying to update from 8.04 to 8.10 using sudo update-manager -d.  The update manager started but stopped with the error message that I need to free up space in /boot.  

Before I do something I can't recover from, what files in /boot are safe to delete?  Here is the output of ls /boot

abi-2.6.20-16-generic             initrd.img-2.6.24-18-generic
abi-2.6.22-14-generic             initrd.img-2.6.24-18-generic.bak
abi-2.6.24-16-generic             initrd.img-2.6.24-19-generic
abi-2.6.24-17-generic             initrd.img-2.6.24-19-generic.bak
abi-2.6.24-18-generic             initrd.img-2.6.24-21-generic
abi-2.6.24-19-generic             initrd.img-2.6.24-21-generic.bak
abi-2.6.24-21-generic             lost+found
config-2.6.20-16-generic          memtest86+.bin
config-2.6.22-14-generic          System.map-2.6.20-16-generic
config-2.6.24-16-generic          System.map-2.6.22-14-generic
config-2.6.24-17-generic          System.map-2.6.24-16-generic
config-2.6.24-18-generic          System.map-2.6.24-17-generic
config-2.6.24-19-generic          System.map-2.6.24-18-generic
config-2.6.24-21-generic          System.map-2.6.24-19-generic
grub                              System.map-2.6.24-21-generic
initrd.img-2.6.20-16-generic      vmlinuz-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak  vmlinuz-2.6.22-14-generic
initrd.img-2.6.22-14-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.22-14-generic.bak  vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-18-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-17-generic.bak


Any help would be appreciated.  Looking forward to try Intrepid.

---

### Post by jheaton5 on 2008-10-22
I wouldn't try to clear this error by removing anything from the boot area.

You are upgrading from hardy to intrepid by upgrading. I decided to backup my data and do a fresh install.  The first thing I did was to download the Live CD and run it from disk to make sure all my hardware still worked.  I played with the Live CD over one weekend and then decided to install.  I was up and running with all data restored in about an hour.

Read [this thread]("http://ubuntuforums.org/showthread.php?t=936696"), which will give you additional information and insight. 

Intrepid has been a pleasure to use.  Every couple of days I get the newest updates from the developers so that just before the stable version is published, I will already have it.

---

### Post by tubunu on 2008-10-23
On a similar note, the update manager says the space in / needs to be freed. I've uninstalled all unnecessary apps and now have 1.6GB of free space there. It still complains about the lack of space. I cannot enlarge the root partition with Partition Editor because the partitions are not contiguous. 

How much space does an upgrade to Intrepid need?

---

### Post by tubunu on 2008-10-23
Update: The manager wanted an additional 71MB of free space. I freed up 200MB (so there's 1.7GB on root partition) and it *still* wants another 24.2MB. Any workaround? :confused:

---

### Post by caro on 2008-10-23
I was able to use Synaptic and remove all the old linux image files from kernel updates.  It freed up over 600MB and I had no problems from there. 

I searched for linux-image-2.6 and removed all the linux-image.2.6*generic files EXCEPT for the current one.  Hope that helps.

---

### Post by tubunu on 2008-10-24
Thanks for advice. Question is, which is the most current linux image file? On my system I have images 16, 17, 18, 19 and 21. Will that be 21 or 16?

EDIT: 
Removed images 16 through 19 and it freed 550MB of space. I'm upgrading as I'm typing this. THANKS. :)

---

