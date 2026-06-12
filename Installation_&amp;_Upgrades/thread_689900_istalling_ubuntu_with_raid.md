---
title: "istalling ubuntu with raid"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by zygoat_D on 2008-02-06
well i have searched and i have found some helpful info but i need more. heres the deal

i know its long but *please* read it.

i have just set up a raid array on my system.
athlon x2 oc'ed to 4800+
3 gb corsair xms2 pro ram
2 x 400 gb seagate baraccuda 7200.10 hd
     in raid 0 through motherboard controller.

ati/amd sb600 south bridge 
ati 2900xt graphics card.


now i have just finished working for about a month to get win xp home 32bit and vista 64 bit both installed and working (there were major issues and i dont want to talk about it!](*,))

in any case it is working now and i am ready to install ubuntu. i have seen that this is called "fakeraid" because it is controlled through the mb raid controller. is this correct?

also i have the raid array split into 4 partitons 1 for each windows install and 1 for each of those installs programs, games, music and such.

i have left a large amount of un-allocated space which is where i would like to install ubuntu. i need to know how to go about this and what i need to do. i ran the live cd and sort of went through the install and it recognized my set up as scsi but saw it as 2 separate drives. although it did say something about "use as one" or something or other.

basically i want to make sure i am doing it right so that i dont wipe my windows installs as they were quite difficult to get working.

thanks in advance for any and all help.

---

### Post by bwtranch on 2008-02-06
Oh, geez, you are a difficult case aren't ya?:) No, just kidding! I personally like fdisk because I am used to it. So, say we were going to part a SCSI drive then fdisk /dev/sda and then p to see the current parts and n for new, etc.  You are going to have to make some changes on your parts and you should do a backup (duh). Make sure you set a filesystem to each part (like ext2 or ext3 or whatever) and don't forget to mount. Lastly make sure GRUB knows what you have done. And I would go with GRUB, LILO doesn't like me!:)

---

### Post by zygoat_D on 2008-02-06
so will this method run linux under raid?

also can you describe the exact phrase to type into the terminal (im not stupid i just havent been working with linux for that long)

and i am a difficult case thanks for taking me on!:p

also in case it matters they are both sata 3gb/s

---

### Post by zygoat_D on 2008-02-07
anybody have any other help or info. 

i would like to run linux under raid and i need to get this shorted out fairly quickly because i need it for my programming class.

thanks for any and all help.

---

### Post by m3tr0g33k on 2008-02-07
In the text installer,you need to make two equally sized partitions of type raid, then choose set-up raid to make them appear as one md device (probably md0) Then further create the partitions of ext3, swap etc. on that md0.The important point is that the raid partitions are created first.

---

### Post by zygoat_D on 2008-02-15
using the fake raid guide on these fourms i got to here.

ubuntu@ubuntu:~$ sudo dmraid -r
/dev/sda: pdc, "pdc_bchdcdf", stripe, ok, 781249792 sectors, data@ 0
/dev/sdb: pdc, "pdc_bchdcdf", stripe, ok, 781249792 sectors, data@ 0
ubuntu@ubuntu:~$ sudo fdisk /dev/mapper/pdc_bchdcdf

The number of cylinders for this disk is set to 97261.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/pdc_bchdcdf: 799.9 GB, 799999787008 bytes
255 heads, 63 sectors/track, 97261 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                  Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_bchdcdf1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/mapper/pdc_bchdcdf2            2551       93242   728483490    f  W95 Ext'd (LBA)
/dev/mapper/pdc_bchdcdf5            2551       48444   368643523+   7  HPFS/NTFS
/dev/mapper/pdc_bchdcdf6           48445       52269    30720000    7  HPFS/NTFS
/dev/mapper/pdc_bchdcdf7           52269       93063   327680000    7  HPFS/NTFS

Command (m for help): 
ubuntu@ubuntu:~$ 



ok thats how far i made it and i am not exactly sure how to proceed. i would like to use the remainder of the disk space for ubuntu.

i have 4 windows partitons
1 xp
1 xp files
1 vista
1 vista files
and would like to use the remainder of the hard drive space for linux. how do i go about doing this?

also i tried to do it using the gui and ended up screwing everything and having to reinstall everyting again. i would like to avoid doing that again. but as a result i think that 2 partitions are created on the hd and i do not know if they are right. i made a swap and a / but i dont know for sure if they are right one is extended and one is logical. which should i be useing and can i get rid of them and start over from my place above? what is the code needed to do that.

thanks to anyone that can lend me a hand!

---

### Post by zygoat_D on 2008-02-16
bump

anybody?

---

