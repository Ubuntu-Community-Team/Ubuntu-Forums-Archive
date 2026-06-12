---
title: "[SOLVED] Gparted do not recognize my partitions!"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by rutz3n on 2008-07-12
My first post =)

I have a windows and a ubuntu partition. The problem is that i formated my windows, and as usual, i got problems to reinstall grub. I tried all the ways possible (you can believe...all the normal and unusual ways described in a lot of foruns), and the only that works was to rewrite the partition table with the fdisk. I did that deleting and creating again the swap partition. Then, reinstalling grub was possible.

I got a Acer Aspire 5100. Sata partition and ATI Radeon graphics...

But now, my ubuntu is totaly messed up (a upgrade since version 6) and i need to reinstall it.

The problem is that **GPARTED DO NOT RECOGNIZE MY PARTITION TABLE**! fdisk does it with no problem! It shows only as one partition.

I got really import things in my disk that i cant lose, so i cant reinstall everything again formating the partitions again with gparted.

Someone have and idea, how could gparted reconize my partitions and reinstall the ubuntu???

I have already tried the alternate cd without success..

Thank you!

---

### Post by SkonesMickLoud on 2008-07-12
Are you able to see the contents of your partitions in Nautilus when you boot to the LiveCD?

---

### Post by rutz3n on 2008-07-13
Yes!!! 

When i boot with the live CD, all my partitions are recognized!

But gparted still do not recognize it.....so i cant reinstall linux in the correct partition =(

Thanks for replying

---

### Post by Pumalite on 2008-07-13
Get Gparted Live CD and partition ahead of time. At install, go Manual and use the prepared partitions:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.

---

### Post by rutz3n on 2008-08-06
Same problem.... =(

Thanks

---

### Post by Pumalite on 2008-08-06
Use rescue cd. It has a partitioner:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by DJ Wings on 2008-08-08
I have the exact same problem. My partition layout is all set, but Ubuntu can't see it. I went with "Manual", and the list was blank! Where should I go from here?

---

### Post by Pumalite on 2008-08-08
Post your specs and:
sudo fdisk -lu

---

### Post by DJ Wings on 2008-08-08
Dell Inspiron E1505N, entry level specs. I've had the same partition layout installed for months (with different distros installed) with no issues.
fdisk runs into issues:
"Unable to seek on /dev/sda"
A quick Google ran into [this.](http://www.linuxquestions.org/questions/linux-desktop-74/unable-to-seek-on-devsda-614966/) I'm trying GPart as we speak.
Update: No luck.

---

### Post by gonorrento on 2008-08-08
Same problem here! If anyone can help I'll really appreciate.

fdisk -lu output:


ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6bdd6bdd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   152151614    76075776    7  HPFS/NTFS
/dev/sda2       152151615   261361484    54604935    c  W95 FAT32 (LBA)
/dev/sda3       261361485   312576704    25607610    f  W95 Ext'd (LBA)
/dev/sda4       310424058   312576704     1076323+  82  Linux swap / Solaris
/dev/sda5       261361611   310423994    24531192   83  Linux

---

### Post by gonorrento on 2008-08-08
SOLVED! (at least for me)

I just install testdisk ( you can do it even using LiveCD; just add UNIVERSE repository ) and for my surprise there was an error in my partition table!!!

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  9470 254 63  152151552
 2 P FAT32 LBA             9471   0  1 16268 254 63  109209870
 3 E extended LBA         16269   0  1 19456 254 63   51215220
 4 P Linux Swap           19323   1  1 19456 254 63    2152647
[SIZE="3"]**Space conflict between the following two partitions**[/SIZE]
 3 E extended LBA         16269   0  1 19456 254 63   51215220
 4 P Linux Swap           19323   1  1 19456 254 63    2152647
   X extended             16269   0  2 19322 254 63   49062509
 5 L Linux                16269   2  1 19322 254 63   49062384


and for my happiness testdisk solve it as a charm!

---

### Post by anlag on 2008-08-08
I've got a similar problem, in that my partition table seems to be messed up a bit. GParted only sees my entire drive as one big chunk of unallocated space. I do however have a fully working Ubuntu installation which I'm accessing now, but the Windows installation I just created now can't be booted into. It seems to me this could likely be connected to the GParted problems.

Posted earlier about the whole situation, which may contain useful background:

[http://ubuntuforums.org/showthread.php?t=884125](http://ubuntuforums.org/showthread.php?t=884125)

In short, I had Ubuntu installed and then installed WinXP on a designated space for it. To do so I had to disable ACHI in BIOS (have a SATA hard drive), and remove my swap partition (too many partitions for Winsetup). Without GParted recognizing my partitions I'm not sure how to recreate it!

As requested:

anlag@casper:~$ sudo fdisk -lu
[sudo] password for anlag: 
omitting empty partition (5)

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x38da4910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78109919    39054928+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        78124095    79120124      498015   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3        83120310   390716864   153798277+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4       358715385   390716864    16000740   83  Linux
Partition 4 does not end on cylinder boundary.
/dev/sda5        83120436   358699319   137789442   83  Linux


Doesn't look great does it?! Any ideas? Saw a program called testdisk which might help, but I'm somewhat cautious to jump into it without a second opinion.

---

### Post by Pumalite on 2008-08-08
TestDisk is the best Patition Table fixer around. Backup everything before you start. (if you can)

---

### Post by anlag on 2008-08-08
Okay then, had a look and think I've arrived at what to do. Testdisk finds the Windows partition as well as my three Linux partitions, hell, even the fourth one (the swap) which I had to delete before installing Windows!

Now, I previously had set it up so Win, /boot and swap were primary partitions, while /home and / were logical. For some reason testdisk now won't let me set any other partition than /home to logical so I guess I'll do that. And accept the deletion on swap ("again") - I can always recreate it from gparted when the partition tables are fixed again. I figure I can't well assign four primary partitions now, as I won't be able to make an extended one later then.

A thought, should the Windows partition be set as bootable? Does it need to, when GRUB is set to load from an own /boot partition?




TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1  4862  29 63   78109857
 2 P Linux                 4863   0  1  4924 254 63     996030
 3 E extended              5174   0  1 24320 254 63  307596555
 4 P Linux                22329   0  1 24320 254 63   32001480
Space conflict between the following two partitions
 3 E extended              5174   0  1 24320 254 63  307596555
 4 P Linux                22329   0  1 24320 254 63   32001480
   X extended              5174   0  2 22327 254 63  275579009
 5 L Linux                 5174   2  1 22327 254 63  275578884




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [ Backup ]
                            Try to locate partition



***


TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  4862 254 63   78124032
P Linux                 4863   0  1  4924 254 63     996030
D Linux Swap            4925   0  1  5173 254 63    4000185
L Linux                 5174   2  1 22327 254 63  275578884
P Linux                22329   0  1 24320 254 63   32001480








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock Recover, 16 GB / 15 GiB


***

TestDisk 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63

     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  4862 254 63   78124032 
 2 P Linux                 4863   0  1  4924 254 63     996030
 3 E extended LBA          4925   0  1 22328 254 63  279595260
 4 P Linux                22329   0  1 24320 254 63   32001480
 5 L Linux                 5174   2  1 22327 254 63  275578884










[  Quit  ]  [Search! ]  [ Write  ]
                       Write partition structure to disk





Partition legend... 

HPFS-NTFS is obviously Windows. Out of the partitions simply labelled 'Linux', the smallest (996k sectors, 512 MB) is /boot, the next one (32M sectors, 16 GB) is /, and the big ******* (276M sectors, ~130 GB) is /home.

Am absolutely dead tired now and will proceed in the morning, any input before then such as critical warnings I'm about to ruin my system... most welcome.

---

### Post by DJ Wings on 2008-08-08
gonorrento, you're awesome. Testdisk did the trick, and now I'm typing this from Ubuntu 8.04.

---

### Post by rutz3n on 2008-08-11
Finally i could fix it! Thanks GONORRENTO!!! Thanks to all!

My first approach, was using a bootable CD of windows XP, then i used the "fixboot" command. With that, the GPARTED start finding my partitions!! 

But in 94% of the instalation (of Ubuntu 8.04), always occur *"could not execute grub-install (hd0).  This is a fatal error."*

So, i tried your approach.... using **TESTDISK** and rewriting the partition table, everything WORKED PERFECT!!!!!

Thanks a lot, to everyone =)

---

### Post by anlag on 2008-08-13
For reference, testdisk fixed my partition tables just fine as well.

The reason I couldn't boot into Windows was something else, namely (again) its lack of default ACHI support for SATA disks.

---

### Post by Diabolis on 2008-09-26
Same problem, same solution. Thanks all.

```
sudo testdisk
create
proceed
partition table type: Intel
analyse
proceed
look for Vista partitions? no (because I don't have it)
Enter: to continue
Write partition table, confirm? yes
```

---

