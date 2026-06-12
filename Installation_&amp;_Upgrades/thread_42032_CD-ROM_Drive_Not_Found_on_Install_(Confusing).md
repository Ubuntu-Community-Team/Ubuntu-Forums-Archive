---
title: "CD-ROM Drive Not Found on Install? (Confusing)"
date: 2005-06-15
forum: Installation &amp; Upgrades
---

### Post by Rellik on 2005-06-15
Hi!  I'm attempting to install Ubuntu to a partition on a secondary drive (Windows XP Home is installed on my primary hard drive).  A dual-boot is the goal.

After getting my computer to begin the Ubuntu installation (from CD), it was going through fine when it tells me that it isn't able to locate any valid CD-ROM drive.  I'm using a "PHILIPS DVD+-RW DVD8631", and I don't believe it came with any floppy disk full of drivers or anything.  Oh yeah, and it also said it did not find a valid Floppy Drive - the Floppy Drive I use (the name listed under "All disk drives" is "Floppy Disk Drive") is working, so I'm not quite sure what's going on here.

If anyone has any insight onto this issue, I would be grateful for your help.

Also, quick question: my data is safe, right?  As long as I am careful in the installation, I don't need to worry about Ubuntu's installation messing with the data in the drive outside of the partition I am installing it to?  It will need to reformat the partition as it is currently NTFS.  Thanks!

---

### Post by imightbegiant on 2005-06-16
Post the contents of your fstab file. This file is configuration for all hard disks, optical disks, etc. You get this by:
```
cat /etc/fstab
``` 

Also post the devices:
```
ls -l /dev|grep hd|awk '{print $9," ",$4}'|grep hd
``` 

> Also, quick question: my data is safe, right? As long as I am careful in the installation, I don't need to worry about Ubuntu's installation messing with the data in the drive outside of the partition I am installing it to? 

yep, as long as you tell the installer not to mess with your other partitions, the data won't be going anywhere.

---

### Post by Rellik on 2005-07-03
[QUOTE=imightbegiant]Post the contents of your fstab file. This file is configuration for all hard disks, optical disks, etc. You get this by:
```
cat /etc/fstab
``` 

Also post the devices:
```
ls -l /dev|grep hd|awk '{print $9," ",$4}'|grep hd
``` 

 

yep, as long as you tell the installer not to mess with your other partitions, the data won't be going anywhere.[/QUOTE]

Thanks for the answer to the partition question!

Also, how do I run those commands in Windows XP?  I don't know if I can complete the Ubuntu installation without it being able to recognize the disc drive - or can I?  I'll try it if it's possible - seems like it would need a cd drive or floppy drive to function.

---

