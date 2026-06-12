---
title: "GRUB fails to install in 8.04"
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Bobatron on 2008-11-29
I was using 8.10 but due to graphical problems decided to try 8.04 but installation fails at 96% when it tries install GRUB


cant remember exact message just something like GRUB has failed to install on hd0 then it runs 8.04 off the CD and it works fine but just wont install the dam thing.



I checked the CD's integrity and it said it was fine.




Only thing I can think of is to try installing it with the alternative text installation CD but doubt it would make a difference

---

### Post by caljohnsmith on 2008-11-29
How about in the last step of the installation, click the "advanced" button, and specify "/dev/sda" as the location to install Grub; I saw someone recently who had the same Grub install error as you, and that's how they worked around that bug. If for some reason that doesn't work, another solution that has worked for many people is:

[http://ubuntuforums.org/showthread.php?t=893156](http://ubuntuforums.org/showthread.php?t=893156)

Let me know if either of those methods work for you. :)

---

### Post by mikewhatever on 2008-11-29
Tell us more about your computer specs and setup, also, boot from the live cd and post the output of 
<sudo fdisk -l> (without <>) from Applications -> Accessories -> Terminal.

---

### Post by Bobatron on 2008-11-29
> **mikewhatever said:**
> Tell us more about your computer specs and setup, also, boot from the live cd and post the output of 
<sudo fdisk -l> (without <>) from Applications -> Accessories -> Terminal.


Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)




And I'll try using that line of code in advanded installation now

---

### Post by Bobatron on 2008-11-29
> **caljohnsmith said:**
> How about in the last step of the installation, click the "advanced" button, and specify "/dev/sda" as the location to install Grub;


Did this and it worked like a charm, thankies :D

---

