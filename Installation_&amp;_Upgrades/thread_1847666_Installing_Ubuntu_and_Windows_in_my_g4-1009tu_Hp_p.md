---
title: "Installing Ubuntu and Windows in my g4-1009tu Hp pavilion Note-book?"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by iyan90007 on 2011-09-21
i tried installing ubuntu as soon as i installed ubuntu. My hard drive is a 500GB one. 

i created a primary partition for windows of 100GB and left the other as NTFS formatted one.

then i started installing ubuntu.

At the place of partitioning in ubuntu installer i tried installing in the leftout hard drive space. i formatted it to ext3 with 65GB. As soon as it is done, a 65GB partition was created with ext3 format and the leftout space is not shown as "unallocated space" :confused: . i canot allocate SWAP also. at this juncture i stopped my installation.

My windows also got corrupted and the whole hard drive got corrupted.

can anyone please tell me a way to install it.:(

---

### Post by Mark Phelps on 2011-09-21
I'm confused -- you created two partitions on your drive, BOTH formatted NTFS?  Or, you created two NTFS partitions and left some space unformatted? Which of these did you do?

Also, why did you select Ext3 when the default filesystem is Ext4?

And, I don't know why your Windows install got corrupted unless you mistakenly chose the Windows partition for your Ubuntu install -- something easy to do given the confusing nature of the current Ubuntu installer.

Anyway, I would suggest the following:
1) Create a 50GB NTFS partition for Win7 install
2) Create a second NTFS partition for data -- make it any size you want
3) Leave space on the drive for Ubuntu -- 50GB is more than enough
4) Install Win7 to the first partition.
5) BEFORE you install Ubuntu, go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You can use this later to repair Win7 boot problems and to restore the original MBR.
6) Install Ubuntu to the free space -- being careful that the installer does not select your Window partition

When you're done and reboot, if you boot directly into Ubuntu without seeing a GRUB menu, then reboot holding down a SHIFT key.  This will force the display of a GRUB menu.

If you don't see an entry for Windows 7 in the GRUB menu, then once into Ubuntu, open a terminal and enter "sudo update-grub". This will regenerate the GRUB menu and should add an entry for Windows 7.

---

### Post by iyan90007 on 2011-09-21
> **Mark Phelps said:**
> I'm confused -- you created two partitions on your drive, BOTH formatted NTFS?  Or, you created two NTFS partitions and left some space unformatted? Which of these did you do?

Also, why did you select Ext3 when the default filesystem is Ext4?

And, I don't know why your Windows install got corrupted unless you mistakenly chose the Windows partition for your Ubuntu install -- something easy to do given the confusing nature of the current Ubuntu installer.

Anyway, I would suggest the following:
1) Create a 50GB NTFS partition for Win7 install
2) Create a second NTFS partition for data -- make it any size you want
3) Leave space on the drive for Ubuntu -- 50GB is more than enough
4) Install Win7 to the first partition.
5) BEFORE you install Ubuntu, go into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  You can use this later to repair Win7 boot problems and to restore the original MBR.
6) Install Ubuntu to the free space -- being careful that the installer does not select your Window partition

When you're done and reboot, if you boot directly into Ubuntu without seeing a GRUB menu, then reboot holding down a SHIFT key.  This will force the display of a GRUB menu.

If you don't see an entry for Windows 7 in the GRUB menu, then once into Ubuntu, open a terminal and enter "sudo update-grub". This will regenerate the GRUB menu and should add an entry for Windows 7.

Thanks
i hav some doubts. i have 5 partitions in my windows 7. Of which two are primary partitions and three are shown as logical drives. 

During ubuntu installation it shows only two partitions, one has windows(100GB NTFS) and other has the remaining harddrive space. 

Last time i installed on the later one and the whole thing went wrong.

i want to know whether i have to resize windows partition or the other one.

Is der a difference btw Shrink volume and create a new volume in windows partition manager?

---

### Post by Mark Phelps on 2011-09-21
OK ... if all five partitions are Primary, then you have that dreaded situation knowns as Dynamic Disks -- and you can NOT install Ubuntu in that situation.

This can happen easily if you have a drive with the maxmimum of four Primary partitions and you FORCE the creation of another one.  MS Windows will then (after an obscure prompt) convert ALL the partitions to Dynamic Disks.

Even if you remove the extra partition(s), I don't believe that Win7 provides a way to convert the Dynamic Disks back to Simple Volumes.  There are third-party utilities that will do this, but I haven't used any of them and don't know if "data loss" will happen if you do the conversion.

---

### Post by iyan90007 on 2011-09-22
> **Mark Phelps said:**
> OK ... if all five partitions are Primary, then you have that dreaded situation knowns as Dynamic Disks -- and you can NOT install Ubuntu in that situation.

This can happen easily if you have a drive with the maxmimum of four Primary partitions and you FORCE the creation of another one.  MS Windows will then (after an obscure prompt) convert ALL the partitions to Dynamic Disks.

Even if you remove the extra partition(s), I don't believe that Win7 provides a way to convert the Dynamic Disks back to Simple Volumes.  There are third-party utilities that will do this, but I haven't used any of them and don't know if "data loss" will happen if you do the conversion.

 If i am going for complete reinstallation(formatting windows 7) how should i give the partitions for 500 GB?

---

### Post by Mark Phelps on 2011-09-22
I would do the following:
1) Remove the existing Windows partition(s) from the drive
2) Create a new NTFS partition of 50GB (at most)
3) Install Win7 to that partition
4) Once Win7 is working, use the Disk Management utility to create an NTFS data partition -- making it whatever size you want.
5) Reboot using the Ubuntu CD and install to the free space

---

