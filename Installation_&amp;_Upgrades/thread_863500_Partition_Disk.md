---
title: "Partition Disk"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by scorphg on 2008-07-18
All,
I have a dual 1ghz old machine i am installing ubuntu 8.04 on...
the disk is a rather new 320GB western digital... after the first install i got an error 18.  I looked that up now, manually partitioned the hard drive and now am getting error 15...
What should I do for partitioning this drive?  Where should the boot loader go?  
my disk is /dev/sda...
i tried to partition it with 15gb for /boot (/dev/sda1) and put the boot loader there... that is where i am now....

any suggestions?
thanks in advance

---

### Post by Pumalite on 2008-07-18
Are you installing only Ubuntu?

---

### Post by scorphg on 2008-07-18
yes only ubuntu...
I have tried the guided - entire disk once,
then the manual effort...

---

### Post by Pumalite on 2008-07-18
If you can boot a Live CD: post:
sudo fdisk -lu

---

### Post by scorphg on 2008-07-18
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd438bdc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    69995204    34997571   83  Linux
/dev/sda2        69995205    74991419     2498107+  82  Linux swap / Solaris
/dev/sda3        74991420   144986624    34997602+  83  Linux
/dev/sda4       144986625   625137344   240075360    5  Extended
/dev/sda5       144986688   214981829    34997571   83  Linux
/dev/sda6       214981893   284977034    34997571   83  Linux
/dev/sda7       284977098   354972239    34997571   83  Linux
/dev/sda8       354972303   424967444    34997571   83  Linux
/dev/sda9       424967508   494962649    34997571   83  Linux
/dev/sda10      494962713   544732019    24884653+  83  Linux
/dev/sda11      544732083   594501389    24884653+  83  Linux
/dev/sda12      594501453   625137344    15317946   83  Linux

---

### Post by scorphg on 2008-07-18
not sure what the Solaris partition is...

---

### Post by scorphg on 2008-07-18
not sure what to do now... i can try the install, but what do i do for partitioning?

thanks

---

### Post by Pumalite on 2008-07-18
Get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it. Delete everything in your drive and format ext3.
Install Guided>Use Entire Disk

---

### Post by scorphg on 2008-07-18
ok will try that...
thanks

---

### Post by scorphg on 2008-07-19
didnt work... install went ok,
however on reboot get error 18

---

### Post by richardjennings on 2008-07-19
This is a problem with your bios not being able to support the size of your harddisk.

What exact model laptop is it. I'll try and find either a bios update to support the new drive, or maybe there are some bios options you can change that will make the drive work correctly.

---

### Post by scorphg on 2008-07-21
Well, I thought i would update everyone on the solution to this...
I had to actually use another smaller hard drive to use for the installation and have the 320gb drive as spare disk space.  
The smaller drive was a 60gb western digital... the setup went flawless.

---

### Post by Pumalite on 2008-07-21
Could be the BIOS or the cable or both.

---

