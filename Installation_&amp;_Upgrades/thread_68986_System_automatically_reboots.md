---
title: "System automatically reboots"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by Yakhunter on 2005-09-24
Whenever I try to do an install or even boot off the live CD I only get to the boot screen and press enter, and my machine just reboots every time.  It gets through only like two initializing steps before this happens.

I have no unusual hardware, I'm running an intel Celeron on a generic compaq presario with no upgrades, so there should be nothing unusual about the hardware.

Any Suggestions?

---

### Post by papangul on 2005-09-25
i'm not sure but you may try to create a swap partition beforehand and mount the swap partition on getting the prompt in the live cd. have you tried linux before? Do you have a swap partition?

---

### Post by Yakhunter on 2005-09-26
Sorry, I don't know what a swap partition is.

---

### Post by papangul on 2005-09-26
Swap partition is used to swap pages to and fro from ram. You need to create a partition 1-2 times the size of your ram. 
1. Defragment the windows C: drive.
2. if you have FAT32 C: drive use fips **following instructions**(and don't forget to defragment C: before trying to free space) to create a partition 1-2 times the size of your ram: [http://www.igd.fhg.de/~aschaefe/fips/](http://www.igd.fhg.de/~aschaefe/fips/)
3.If you have a floppy drive, create a linux boot floppy: [http://www.igd.fhg.de/~aschaefe/fips/](http://www.igd.fhg.de/~aschaefe/fips/)
4. Boot with this floppy and if you have a normal hdd just run the following command:
 ```
fdisk /dev/hda
```
5. See the fdisk help by typing 'm' and see the partition table by typing 'p', you can change the  id of the partition you intend to use as swap by typing 't' and pressing enter.
6. From command prompt type ```
mkswap /dev/hda2
```
7. Boot with the Ubuntu disk , at the boot promt type: ```
swapon /dev/hda2
```
**I have assumed hda2 is your intended swap partition**.

---

