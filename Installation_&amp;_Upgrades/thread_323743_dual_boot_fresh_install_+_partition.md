---
title: "dual boot fresh install + partition"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by manutdfan2850 on 2006-12-22
hi i am totally new to this and need help installing

i want a to format my hard disk and install both xp home and ubuntu. i would like to dual boot and also be able to share files between my partitions. i heard there was a way to do this.

could someone plz outline the installation procedure to me and how to partition my HD. its a 60 gb hard drive so could you also plz say about how much i should allow for the XP partition, and how much for the ubuntu partition?  also what file systems should i use for the partitions? ntfs or fat? plz help

thanks in advance

ps i have a toshiba satellite s206 : p4 2.8ghz, 512mb ram, 60 gb hd (in case that helps)

---

### Post by bulldog on 2006-12-22
It's depending on which OS you gonna use most,I presume windows.
Make a 30GB windows NTFS partition.
Create a 10GB FAT32 to exange data between the two OS's.
Create a 1GB swap file format as swap.
Make the rest your ubuntu partition and format it ext3

Best to do this with the gparted live cd,it's only a 30MB download.
Burn this to a cd-r and boot from it.

Install windows before you install ubuntu otherwise you get GRUB trouble.

---

### Post by manutdfan2850 on 2006-12-23
i was considering increasing the FAT32 partition to like15 or 20 gb to increase the amount of data i could share between xp and ubuntu. is that safe/ recommended? for example, i would like to share my music and video collection between both OS. what do you think? 

also what is the function of the swap partition? i read somewhere 512 mb is ok or should i stick with 1gb

thanks

---

### Post by bulldog on 2006-12-23
You can **read** all the data that is stored in windows so you can access it any time.
You can't **write** data to a NTFS partition.

I'm not very fund of FAT32 file system but it comes in handy some times :D 
Another possibility is to make a /home partition and forget about the FAT32.
There's a driver,which should be installed in windows,and you can perfectly read and write to your ext3 partitions from windows.
In that case I should make windows 30GB and 1GB swap and a /  (root) 10GB and the rest of the space a /home partition.
If you have to reinstall ubuntu for some reason, the /home will keep your data and settings.

Swap is the same as the windows page file,it's used when your physical RAM is used.

---

