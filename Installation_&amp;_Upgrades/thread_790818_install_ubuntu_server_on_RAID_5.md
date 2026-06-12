---
title: "install ubuntu server on RAID 5"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by pavlizz on 2008-05-11
Hello there,

I'm trying to install ubuntu server and I create 2 raid 5 one for my root dir and one for the swap (I have 3*500GB sata disks)
I put boot flags and on the 3 portions that they belongs to root
All of my partitions are primary.
The installation continuous normally and I get an error that is not able to install GRUB On my system

What I can to to get my system working ?

---

### Post by vorgusa on 2008-05-11
I believe I have run into this problem before.  Are you using Hardware Raid or trying the software raid?  You can not install your OS on the software raid because the OS is what handles the hard drives.  When the computer tries to boot it will not be able to understand the partitions.  You need a full out Raid Card like an Areca 1208.  You can install the OS on a single hard drive and then create a RAID 5 partition to store files on in the installer.

---

### Post by pavlizz on 2008-05-11
I'm trying to build a software raid 

I installed previously Ubuntu on soft raid exactly  raid1

I think the system it can't see the raid as one devise and  in cant install GRUB on it

The error that I see it says

Error executing "grub-install (hd0)" failed.
this is Fatal Error

---

### Post by vorgusa on 2008-05-11
Not sure about if the OS can boot from a software Raid 1 but it makes sense that it could since it is just two identical hard drives.  Raid 5 will put parts of every files on all three of your hard drives and will not be able to work properly... I have looked into it before because I wanted to do Raid 0 on my desktop, and ran into the same problem.  After doing a bunch of googling I ran into a site that said Ubuntu does not support install on Software Raids.

---

### Post by pavlizz on 2008-05-11
If I install my system on a separate disk and after create the RAID 5 on the disks it will work.

What happens if the separate disk burns? I will loose all my data ? 

If I make a new install Can I rebuild the raid and not loose a single bit of data ?

---

### Post by vorgusa on 2008-05-11
Your OS will not be saved by the hard disk dieing but all the data on the RAID 5 will be able to survive a hard disk failure. 

"If I make a new install Can I rebuild the raid and not loose a single bit of data ?"  

If your OS dies and you want to get your data after reinstalling the new OS should be able to find it.. You might want to do some googling or just test it out before relying on it.  Or see if someone else knows.

---

### Post by pavlizz on 2008-05-11
I will create 3 raid 1 RAID 5 for my data one raid5 for my swap and and raid1 for my boot dir

I believe that is the best configuration

---

### Post by pavlizz on 2008-05-11
Nothing yet :(

I have create 3 raid arrays 

first RAID 1 100 MB for the /boot directory
second RAID 5 498 GB for the / root directory
Third RAID 5 2 GB for SWAP

The installation continues normally and finish But the system is not booting

NOW I get this error 

isolinux: Disk error 01, AX = 0201, drive 80

---

### Post by vorgusa on 2008-05-11
any reason why you have the swap partition on the RAID 5... you should not gain much by having that on the RAID 5, since there is nothing to backup.  Try moving that over to the RAID 1 drives

---

### Post by samb0057 on 2009-08-07
I have this same problem

3x 500gb drives on silicon 3114 controller using software raid

/boot - raid 1
/ - raid 1
/storage - raid5

it will not boot, it tries to boot from the cd. using the ubuntu cd i pressed boot from first hard disk and got "disk error 01, ax = 0201"

---

### Post by bwdavis on 2009-08-11
New to linux.  Have 8.10 desktop installed on my laptop.
 
Current goal is to setup samba server for file and print for windows.  Trying to install 9.04 i386 server on 3x 20G SCSI2 HDD's - followed instructions for setting up raid 5, I set up 2 arrays, #0 2.4GB for swap, 16GB for data, set filesystems, root mount point, set root file partition to bootable, then set up raid5 arrays.  Installs great, but will not boot.  once installation is complete, and I remove CD, reboots to black screen with cursor blink.  no message at all.  
Reading through here, should I just install Ubuntu server on the first hdd, and then make a Raid5 array for the root file system on the remaining space? 
Or can someone tell me how to get this thing to boot or point me in the right direction?
 
Thanks
Bruce

---

