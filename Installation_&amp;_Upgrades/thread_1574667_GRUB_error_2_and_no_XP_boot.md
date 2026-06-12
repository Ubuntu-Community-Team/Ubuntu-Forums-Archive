---
title: "GRUB error 2 and no XP boot"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by Bernard_ivo on 2010-09-14
Dear all, 

I need assistance in the following as I haven't managed how to fix the problem (I've read some How to etc)

I was trying to make fresh install of Ubuntu 10.4 on dual boot system running XP and Ubuntu 8.4 However I also wanted to resize the partitions first and then install the new ubuntu. I ran Live CD and tried to resize and reformat partitions: adding few GB to the XP partition, deleting one fat 32 (previously used to transfer files between XP and Ubuntu). The result was that within the Ubuntu partitions I had two small unallocated parts in different parts of the drive which I wanted to use for swap. The Live CD did not allow me to do that and showed Unable to satisfy all constraints on the partition. Then I started Gparted from the Live cd. Then I deleted all linux partitions and tried to use the newly unallocated to properly set up /,/home,/swap etc. I managed, though some 1.2MB are still unallocated (I can survive this). 

However after resizing and reformating I wanted to run windows so it is able to check its new size, check for errors and then to go back installing ubuntu. Obviously I spoiled the GRUB since all Ubuntu partitions were reformated and at startup I recieve GRUB ERROR 2 and no way to start Windows. 

Any suggestions what to do?
I want to start the XP for the above reason to check its new partition size. If not possible should I try to install Ubuntu and hope that GRUB will somehow be fixed during the install, will let me in Windows and Windows will not be messed?

Update: I have installed ubuntu and GRUB works, I can access my XP and CHKDSK showed no errors. Ubuntu seems to work properly as well.

Cheers
Ivo

---

