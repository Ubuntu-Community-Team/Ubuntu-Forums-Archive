---
title: "Ubuntu Netbook installation problem after two failed installation attempts"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by rebelsoul on 2010-09-28
Hello, 

I am newbie to Ubuntu, i was trying to install ubuntu on my EEE PC 1005HA. I used Ubuntu netbook and followed every procedure and in the end managed to run a dual boot system (Wind xp and Ubuntu). While working on ubuntu i allowed updates, after updates and reboot when i tried to logged in to the system, it  gave me Unknown device Grub Rescue message. I tried to run EEE PC recovery mode, but it was not working. So after spending many hours and trying to solve the problem. i did another installation on one of  the other partitioned through live cd. While doing that i selected option Where Ubuntu and other OS could work together. That installation was successful and i was able to log on two Ubuntus and one win xp. However, tempted by my curiosity i tried to revert the whole system back by EE PC recovery tool, which was working at that time. The end result of all this step was that my whole system crashed again, as grub is corrupted and this time error message is Unknown file system. I tried to follow the solution provided on this forum but no avail and now my system after getting boot from live cd become busy after few minutes. I could see a huge number of my partitions which is impossible as i have only 160 GB and there are almost 60 partition of 34 GB each :mad:
Here is a result after fdisk.
  [HTML]ubuntu@ubuntu:~$ sudo fdisk -lu
Warning: omitting partitions after #60.
They will be deleted if you save this partition table.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0261f0b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    81160201    40580069+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        81162238   302230844   110534303+   f  W95 Ext'd (LBA)
/dev/sda3       302230845   312480314     5124735    c  W95 FAT32 (LBA)
/dev/sda4       312480315   312576704       48195   ef  EFI (FAT-12/16/32)
/dev/sda5       151123518   188512263    18694373    7  HPFS/NTFS
/dev/sda6       224845741   291837868    33496064   83  Linux
/dev/sda7       148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda8        81162240   148154367    33496064   83  Linux
/dev/sda9       148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda10       81162240   148154367    33496064   83  Linux
/dev/sda11      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda12       81162240   148154367    33496064   83  Linux
/dev/sda13      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda14       81162240   148154367    33496064   83  Linux
/dev/sda15      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda16       81162240   148154367    33496064   83  Linux
/dev/sda17      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda18       81162240   148154367    33496064   83  Linux
/dev/sda19      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda20       81162240   148154367    33496064   83  Linux
/dev/sda21      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda22       81162240   148154367    33496064   83  Linux
/dev/sda23      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda24       81162240   148154367    33496064   83  Linux
/dev/sda25      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda26       81162240   148154367    33496064   83  Linux
/dev/sda27      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda28       81162240   148154367    33496064   83  Linux
/dev/sda29      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda30       81162240   148154367    33496064   83  Linux
/dev/sda31      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda32       81162240   148154367    33496064   83  Linux
/dev/sda33      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda34       81162240   148154367    33496064   83  Linux
/dev/sda35      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda36       81162240   148154367    33496064   83  Linux
/dev/sda37      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda38       81162240   148154367    33496064   83  Linux
/dev/sda39      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda40       81162240   148154367    33496064   83  Linux
/dev/sda41      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda42       81162240   148154367    33496064   83  Linux
/dev/sda43      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda44       81162240   148154367    33496064   83  Linux
/dev/sda45      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda46       81162240   148154367    33496064   83  Linux
/dev/sda47      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda48       81162240   148154367    33496064   83  Linux
/dev/sda49      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda50       81162240   148154367    33496064   83  Linux
/dev/sda51      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda52       81162240   148154367    33496064   83  Linux
/dev/sda53      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda54       81162240   148154367    33496064   83  Linux
/dev/sda55      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda56       81162240   148154367    33496064   83  Linux
/dev/sda57      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda58       81162240   148154367    33496064   83  Linux
/dev/sda59      148154431   225539472    38692521    7  HPFS/NTFS
/dev/sda60       81162240   148154367    33496064   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf49f8b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     2015231     1007600    b  W95 FAT32
[/HTML]

Kindly help me to restore my system to it previous state and restore Grub.

---

### Post by mikewhatever on 2010-09-29
This is very odd. I think something, Gparted or the EEE recovery tool must have corrupted the partition table with numerous entries. There aren't really 60 partitions on the hdd, as every partition starting from sda7 has the same starting and ending sectors. Is there an external recovery media provided by Asus (not the recovery partition)?

---

### Post by rebelsoul on 2010-09-29
thank you for replying. Yes, the system came with a recovery disk however i don't have an external dvd rom to run the recovery software. So, right now i have to fix everything from live cd ;).

---

### Post by 23dornot23d on 2010-09-29
Have a look at Testdisk 6.11  .... just analyze your disk first and make a backup ....

But do not do any changes ..... 

Analyze - Intel/Pc - Quit - Quit .... take a screenshot or record the data it gives back .... takes a while ...

examining the drive ..........

This is just to see what it can find ...... you do not need to commit to anything here ....

But it has saved my drive before ....... somehow seems to have gone into a loop and done the same thing
over and over ......

Get as much info about the drive structure as you can before comitting to anything ..... unless there is nothing
of importance on the drive ...... or you have a backup .........

**Last thing is ... Can you get or borrow a USB DVD device ..... to restore your system ..... **

Testdisk may get the disk back to normal ..... 

Just by deleting all the extra partitions using TESTDISK ..... 9 though to 60 ,,, may work at restoring the normal structure.

but thats your choice ....... see if you can back anything/everything up first - if you do not already have a backup ......

---

### Post by mikewhatever on 2010-09-29
Does the live cd work? If it does, you might be able to repair the partition table with testdisk. Install it with 
**sudo apt-get install testdisk**

then run with 

sudo testdisk

[testdisk howto]("http://www.howtoforge.com/data_recovery_with_testdisk")

---

### Post by rebelsoul on 2010-09-30
Thank you guys for replying. I have tried to run testdisk and it worked up to some extent afterwards my system stop responding :(. In my opinion 
1)My system can not process from live cd because of corrupt partition table.
2) Asus EEE Pc are not designed to run ubuntu (i hope that's not the case). 

@23dornot23d, unfortunately i don't have a USB dvd drive, i am trying to get hold of it, so lets see. 

Now the problem is that how i could run complete testdisk without making system busy :) ?
Any suggestions..
Thank you guys for helping me and teaching me something new. Btw, this ubuntu problem has led me to a new learning process :)

---

### Post by mikewhatever on 2010-09-30
> **rebelsoul said:**
> 
1)My system can not process from live cd because of corrupt partition table.

Quite possible, although live cds don't need partition tables to work. For example, Ubuntu would load from a live cd even if there is no hdd inside the computer.

> 2) Asus EEE Pc are not designed to run ubuntu (i hope that's not the case).

That is true. Asus doesn't make computers for Linux, as well as other big vendors, HP, Lenovo, Acer, etc. Dell is the only international vendor that sells computers with Linux, but you might have a hard time finding and buying one.
Despite the above, many EEE pcs have been reported to work well with Ubuntu and other distros, in fact, some distros are specially tailored for eee pcs.

I really hope there is a way to clean up this mess, and that someone here knows how. As the very last resort, you could try using the [Boot and Nuke CD]("http://sourceforge.net/projects/dban/").

---

### Post by 23dornot23d on 2010-09-30
What was the output of testdisk .... did you get any information from it ?

The CD should boot ok .... unless its corrupt .... can you use another Ubuntu CD

Worth trying another liveCD ...... you should test with the liveCD

If the LiveCD works ok then there should be very few issues ......

I have never seen the problem you have had on this forum before with

multiple partitions being created ........ so it may just be a bad CD you have .... burnt,

Hope this helps in some way .....

---

### Post by rebelsoul on 2010-10-02
Update: System has recovered!!!:P
Thank you guys for helping me out. I used Gparted instead of Ubuntu and followed mixture of steps provided at the following link and my common sense.
[HTML]http://www.howtoforge.com/data_recovery_with_testdisk[/HTML] 

Although, currently i have two instances of Ubuntu and one xp running on my machine. However, this was the exact state before my system went down.

P.S: Thank you guys for helping me!! Have a awesome weekend!!!

---

