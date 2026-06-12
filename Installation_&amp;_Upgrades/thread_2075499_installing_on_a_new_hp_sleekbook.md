---
title: "installing on a new hp sleekbook"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by mickynuu on 2012-10-24
hi ive been using ubuntu for a few years now along side windows 7 & i have bought one of the new hp sleekbooks from pc world and would like to install 12-04 or 12-10 alongside windows as i use windows only for corel painter graphics software ....the rest of word processing internet all can be done with ubuntu ....only as its a brand new laptop i have read of a few issues in the forum installing ubuntu to do with the eifs sysytem being locked no bios option and ubuntu not installing correctly ...i can tinker around a little but im no expert to start messing around with rewriting programmes ...will 12-10 install as normal alongside i read there are a few issues fixed as in canonical being able to utilise software with hp that can install ubuntu alonside windows with this eifs system ....i would like to be able to do it as trouble free as possible .....thanks for any info

---

### Post by mastablasta on 2012-10-24
use 12.10 if 12.04 fails. 
here is about UEFI: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
 
is windows installed in EFI mode?
 
i am also a bit confused sinc ei have no idea how the preisntalled windows on new HP was instaleld.
 
oh also you probably have 4 primary partitions and will have to remove one to be able to isntall Ubuntu. i am still investigating which one is best and safest to be removed. Hptools has diagnostics, while windows recovery offers system recovery. i don't have DVD drive to be able to create backup dvd's.

---

### Post by Mark Phelps on 2012-10-24
IF you're serious about dual-booting on a laptop that has Win7 preinstalled, read through the material below BEFORE you do anything else -- this way, you know what you're up against:

Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by mickynuu on 2012-10-24
hmm thanks for the feedback sounds a bit more technical than im capable of  if i completely re formatted the hard drive can i just install ubuntu from usb drive and use only ubuntu or does this system of partitions and windows allocation and hp tools prevent this limiting you to use their system or would it completely overwrite the os to ubuntu i could run windows as a virtual machine from usb but does this eifs system let u acess the bios to boot from usb ?? with a normal machine u can enter bios and chosse your boot from what i can understand hp dont

---

