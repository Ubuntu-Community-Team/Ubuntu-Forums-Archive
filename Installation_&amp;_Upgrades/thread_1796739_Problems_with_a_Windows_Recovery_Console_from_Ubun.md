---
title: "Problems with a Windows Recovery Console from Ubuntu"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by KevinM2k on 2011-07-04
Hi,

I have a packard bell system with (atm) 4 partitions, 
1: PQ SERVICE
2: SYSTEM RESERVED
3: UBUNTU
4: UNALLOCATED (ive tried NTFS and FAT32 here)

the system reserved holds my original windows recovery management tool which will load the system back to factory defaults and when I had WINDOWS as my 3rd drive this worked no problem.

Since i've now removed windows and put ubuntu as the 3rd drive however it will no longer work.

I can boot in to the recovery management window but when it comes to selecting the destination for the recovery to be installed to, there are no options. I am thinking this is because it is expecting /dev/sda3 to be the windows drive and because it isn't doesn't like it.

If I move remove the ubuntu drive and use the space to be NTFS (which would then make it /dev/sda3) I will then lose grub meaning I wont be able to get in to the recovery management console at all.

Has anyone got any ideas? Driving me mad! Just want to get it back to windows so I can sell it :)

---

### Post by mastablasta on 2011-07-04
Then try to get a recovery CD. it can recover (overwrite) grub with windows MBR.

---

### Post by KevinM2k on 2011-07-04
> **mastablasta said:**
> Then try to get a recovery CD. it can recover (overwrite) grub with windows MBR.

It doesn't have a CD drive unfortunately.

---

### Post by KevinM2k on 2011-07-04
I have managed to solve this, thought i'd post in case anyone has same issue:

i tried super grub disk, which didnt work for me, so instead i loaded up the ubuntu live cd.

Reformatted my hdd so I had a 100gb ntfs partition at /dev/sda3 and created a new ext4 partition at /dev/sda4, I then installed the mbr to /dev/sda, then installed ubuntu, this installed grub and gave option of going to recovery console, this then picked up /dev/sda3 as being a windows partition and recovered itself as expected. Then I could remove the ubuntu partition and extend the windows partition from within windows.

---

