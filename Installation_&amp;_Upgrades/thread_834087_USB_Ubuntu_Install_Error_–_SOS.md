---
title: "USB Ubuntu Install Error – SOS"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by fresh69 on 2008-06-19
Hi guys & girls new to the forum so go easy.

The issue at hand is as follows:
Getting an Error on ubuntu 8.04 install to a USB flash drive. Here is the link ([http://blogs.zdnet.com/hardware/?p=1873](http://blogs.zdnet.com/hardware/?p=1873)) i have followed the install instructions to tee but once i get to step 7 the install stops at 5% and comes up with a message box saying: The attempt to mount a file system with type swap in SCS13 (0.0.0), partition #5 (sda) at none failed.You may resume partitioning from the partitioning menu. 

**Steps i have taken so far: **
1. Tried the error check for ubuntu install menu for the live CD comes in good.
2. Reconnected my hard drive to boot up windows to run a format & disk error check on my flash drive comes up good.
3. Have attempted to do the install 4 times and keep getting the same error. 


Computer Specs:
Toshiba Tecra M2 Laptop (Hard Drive Disconnected)
Generic 16gig USB Flash drive 

Please if someone could help.....  :mad:

---

### Post by fresh69 on 2008-06-19
> **fresh69 said:**
> Hi guys & girls new to the forum so go easy.

The issue at hand is as follows:
Getting an Error on ubuntu 8.04 install to a USB flash drive. Here is the link ([http://blogs.zdnet.com/hardware/?p=1873](http://blogs.zdnet.com/hardware/?p=1873)) i have followed the install instructions to tee but once i get to step 7 the install stops at 5% and comes up with a message box saying: The attempt to mount a file system with type swap in SCS13 (0.0.0), partition #5 (sda) at none failed.You may resume partitioning from the partitioning menu. 

**Steps i have taken so far: **
1. Tried the error check for ubuntu install menu for the live CD comes in good.
2. Reconnected my hard drive to boot up windows to run a format & disk error check on my flash drive comes up good.
3. Have attempted to do the install 4 times and keep getting the same error. 


Computer Specs:
Toshiba Tecra M2 Laptop (Hard Drive Disconnected)
Generic 16gig USB Flash drive 

Please if someone could help.....  :mad:

:-({|=

---

### Post by avtolle on 2008-06-19
In step 4 of the linked process, the installer (guided, use entire disk) should have created a /swap partition. The error message makes it seem to me that no /swap partition was created.

EDIT: Rereading the error message causes me to think that while a /swap partition was created, no mount point was created. Take a look at the USB drive again and see if a mount point is given for the swap partition.

---

### Post by metalf8801 on 2008-06-19
Try not installing a swap partion

---

### Post by fresh69 on 2008-06-19
**Options in step 4 within the setup are:**

option 1: Guided-use entire disk linked to SCS13 (0,0,0)(sdal-17.0 generic flash drive
when trying this option 1 im getting the above error message i posted above in my first post.

option 2: Manual >> i selected /dev/sda
When trying option 2 i get a new error message:
No root file system is defined please correct this from the partitioning menu  

**[COLOR="DarkRed"]Any help on this matter would be great guys >>>>[/COLOR]**

---

### Post by oldos2er on 2008-06-19
Define the root file system as "/"

---

### Post by fresh69 on 2008-06-19
Tried the above didnt work same error message. 

**CAN ANYONE HELP PLEASE ????**

---

### Post by Pumalite on 2008-06-19
All you have to do when making the filesystem partition is planting a '/' where it says 'mount point'

---

### Post by fresh69 on 2008-06-19
as stated before still getting same error message

---

