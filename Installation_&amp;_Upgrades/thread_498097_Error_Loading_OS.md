---
title: "Error Loading OS"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by mleman on 2007-07-10
I have been running Gentoo on my server up until this past Monday.  For various reasons I wanted to move to a new distro and decided to try Ubuntu.  I installed the server version, everything went fine but when my PC booted up again I was greeted with a BIOS message saying "Error loading OS".  What I can gather from Google it tells me that my MBR was hosed.  I tried reinstalling several times, manually partitioning the hard disk as well as using the guided partition, but no dice.  I also tried the desktop release, and installing via the live CD.  Same issue.  From here I'm not sure what I can do, I thought repartitioning the hard drive wiped everything out and rebuilt the MBR?  Any suggestions would be appreciated.  Here's the specs on my PC:

AMD Athlon 64 3000+ Processor
512 MB RAM
Gigabyte K8NSPro Motherboard
nvidia 5700 Video card
4 SATA Hard Drives (2 x 120GB, 2 X 250GB)
1 160GB IDE Hard Drive

I keep all my data on the SATA drives, I use the IDE drive entirely for the OS.

Thanks,
mleman

---

### Post by rillip on 2007-07-11
It sounds like grub didn't install correctly.  I'd try and load from the LiveCD and install to the appropriate drive from there, then check the menu.lst and make sure it points to the drive/parition your OS is on. There's also SuperGrub, which I believe has its own LiveCD

---

### Post by jjjhackkk on 2007-07-11
Hi all,

Currently i'm a windows user for yrs, and im planning to try the OS of linux, its either ubuntu 7.04 or fedora 7, any recommendations? what is the best to install? i know its really difficult for me or other first time users to adapt this kind of environment, but i want to learn more other than windows OS.

my current issues like,
- hardware drivers? video/sound cards, printers?
- software applications im using for windows xp, are all of this compatible? e.g. adobe photoshop, real, etc.
- how about like word, excel applications? does this OS has same apps?
- games, e.g, windows based games like warcraft, nbalive, etc.
- currently i also use windows based pocket PC my prob will be synchronization.
- of course stability and realibility?

Hope some reply.

Thanks.

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **mleman said:**
> I have been running Gentoo on my server up until this past Monday.  For various reasons I wanted to move to a new distro and decided to try Ubuntu.  I installed the server version, everything went fine but when my PC booted up again I was greeted with a BIOS message saying "Error loading OS".  What I can gather from Google it tells me that my MBR was hosed.  I tried reinstalling several times, manually partitioning the hard disk as well as using the guided partition, but no dice.  I also tried the desktop release, and installing via the live CD.  Same issue.  From here I'm not sure what I can do, I thought repartitioning the hard drive wiped everything out and rebuilt the MBR?  Any suggestions would be appreciated.

I had similiar problem when I was reinstalling xubuntu due ext3 filesystem corruption, which also originated from the same issue. For some reason the partition tool "gparted" shiped with ubuntu installer do not overwrites anything (even fat32 partitions!), but scavenges anything lying on hd from previous instalations no matter how corrupted they were. I also noticed that every time I tired in the ubuntu installer in the manual setup to erase ext3 partitions and resize and format them again I was getting less and less available space on my hd to place my partitions!

My fix was to reformat into fat32 with "partition magic" the former ext3 partitions, which I planned to use for my xubuntu installation again, then "secure format"/"low format" this fat32 partition, then format ready ext3 "/","/home/" and "swap" partitions with "partition magic" before being able to get clean and working install of ubuntu on my hd with use of "manual setup".

However i also discovered that my "/home/" partition lying between "/" and "swap" got smaller in gparted by 1gb, then it was originally in "partition magic". Now my files on "/home/" partition get corrupted and i experience sudden closures of firefox and thunderbird, but none of my programs is any more disabled by segmentation fault as it was happening when I use to have just only "/" and "swap" partitions.

Maybe "manual" setup for partitions just doesn't work in ubuntu installer, but if the same issue is with "auto" then maybe "gparted" in ubuntu installer is with some bug.

---

### Post by Odrodzona-Sarmacja on 2007-07-11
> **jjjhackkk said:**
> Hi all,

Currently i'm a windows user for yrs, and im planning to try the OS of linux, its either ubuntu 7.04 or fedora 7, any recommendations? what is the best to install? i know its really difficult for me or other first time users to adapt this kind of environment, but i want to learn more other than windows OS.

Yes. Wait until september and get less bugy ubuntu 7.10 release.

> my current issues like,
- hardware drivers? video/sound cards, printers?

If you run livecd from boot (it won't install anything on hd, as the install tool is on desktop when livecd bootup and starts only if you click on its icon), then you know from errors messages or lack of them if it did detect all your hardware or did so correctly. Just get more then 64mb memory before you do it. :)

> 
- software applications im using for windows xp, are all of this compatible? e.g. adobe photoshop, real, etc.

Windows software is not, but surely documents used by windows software is compatible with Linux software. The only thing is that you need to make many sofware instalations to the default ubuntu's software.

> 
- how about like word, excel applications? does this OS has same apps?

OpenOffice software package covers any problems with word, excel and alikes. Ubuntu have the same apps except rar compresion tool. In Ubuntu you can only decompress rar files.

> 
- games, e.g, windows based games like warcraft, nbalive, etc.

In most cases even after installing "cedega" or "wine" the windows games still do not play with full functionality. That's why most people have dual boot windows/ubuntu with both oses.

> 
- currently i also use windows based pocket PC my prob will be synchronization.

Dunno about that, but with dual boot windows/ubuntu there shouldn't be many problems.

> 
- of course stability and realibility?

Do not look for lack of bugs or much stability in ubuntu 7.04. It is horribly unstable release even in opinion of hardened ubuntu users, who will recomend you rather ubuntu 6.10 then 7.04 for your first experience with Ubuntu. Wait until september and get yourself 7.10 version. This 7.10 release should be stable I hope, as stable release in april this year of debian 7.04 occured and ubuntu uses it, as its base.

Good luck! :)

ps. do not use vista on your dual ubuntu/windows boot. :D

---

### Post by mleman on 2007-07-12
> **rillip said:**
> It sounds like grub didn't install correctly.  I'd try and load from the LiveCD and install to the appropriate drive from there, then check the menu.lst and make sure it points to the drive/parition your OS is on. There's also SuperGrub, which I believe has its own LiveCD

I have been trying to find out as much as I can about grub and the MBR the past couple days.  I found this program: [http://www.geocities.com/mbrwizard/index2.html](http://www.geocities.com/mbrwizard/index2.html) which lets you look at and do various things directly to the MBR.  I did not wipe it out, i just poked around to see how it was set up.  According to that program my IDE disk is set to disk number 4 in the MBR.  I then used the Ubuntu live cd to check out the menu.lst file.  This site was helpful in finding that: [http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html](http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html)

After mounting the drive to /mnt and changing the root of the file system I was able to edit menu.lst.  I changed the line that had "hd(0,0)" to "hd(3,0)" (since grub treats the first disk as 0).  This did not solve the problem, I still get the "Error Loading OS" when BIOS is booting the PC.  I have tried running grub-install /dev/hda as per the article above but that did not work either.

> I had similiar problem when I was reinstalling xubuntu due ext3 filesystem corruption, which also originated from the same issue. For some reason the partition tool "gparted" shiped with ubuntu installer do not overwrites anything (even fat32 partitions!), but scavenges anything lying on hd from previous instalations no matter how corrupted they were. I also noticed that every time I tired in the ubuntu installer in the manual setup to erase ext3 partitions and resize and format them again I was getting less and less available space on my hd to place my partitions!

My fix was to reformat into fat32 with "partition magic" the former ext3 partitions, which I planned to use for my xubuntu installation again, then "secure format"/"low format" this fat32 partition, then format ready ext3 "/","/home/" and "swap" partitions with "partition magic" before being able to get clean and working install of ubuntu on my hd with use of "manual setup".

However i also discovered that my "/home/" partition lying between "/" and "swap" got smaller in gparted by 1gb, then it was originally in "partition magic". Now my files on "/home/" partition get corrupted and i experience sudden closures of firefox and thunderbird, but none of my programs is any more disabled by segmentation fault as it was happening when I use to have just only "/" and "swap" partitions.

Maybe "manual" setup for partitions just doesn't work in ubuntu installer, but if the same issue is with "auto" then maybe "gparted" in ubuntu installer is with some bug.

I'm not sure if it's relevant, but the IDE drive I'm trying to install ubuntu on had 3 partitions.  It had a swap partiton, an ext3 partition mounted to /boot, and the / partition formated with reiserfs.  The other 4 SATA discs are formated with xfs.  I don't think this would have cause any problems since I wiped the whole (IDE) drive out and repartitioned it (many times now) during the ubuntu install.  I've even tried booting with the ubuntu live cd, partitioning the drive with fdisk, and then rebooting and installing with the ubuntu server disc.

Earlier today in my troubleshooting I used [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) to run a program to wipe the whole drive and write 0's to the whole thing.  In retrospect I doubt this was helpful since it didn't wipe out the MBR with 0's and I'm pretty sure the issue here is with the MBR/grub.  Anyone have any other suggestions short of trying a different hard disk (which I don't have at my disposal and don't really want to buy)?  Would the presence of my other drives be somehow causing a conflict?

I'm going to try and install gentoo again and see if this is just an Ubuntu issue, I may also install windows but I am reluctant to do that because it takes so long and I'd have to wipe it out again anyways since I refuse to run windows on my server.

Edit:

I tried booted into gentoo from a live cd, partitioned the drive, and made the proper file systems on them.  Then I tried installing ubuntu again, the server verison.  Ubuntu didn't complain about the partitions during install, and it just wanted to format the swap partition again.  However I'm still getting the "Error Loading OS" issue.  I noticed that it is setting up grub with hd(0) still, with no option to change that in the server install.  I booted into the Ubuntu live cd and ran the mbrwiz program again, this is the output from that:

 Disk: 0 - /dev/sda   Size=117G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  0    0    83-Linux   117G   No    No            31  120,053,713

 Disk: 1 - /dev/sdb   Size=117G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  0    0    83-Linux   117G   No    No            31  120,053,713

 Disk: 2 - /dev/sdc   Size=239G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  0    0    83-Linux   239G   No    No            31  245,111,706

 Disk: 3 - /dev/sdd   Size=239G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  0    0    83-Linux   239G   No    No            31  245,111,706

 Disk: 4 - /dev/hda   Size=153G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  0    0    83-Linux    39M   Yes   No            31       40,131
  1    1    82-LxSwap  1.5G   No    No        40,162    1,510,110
  2    2    83-Linux    98G   No    No     1,550,272  100,004,625

 Disk: 5 - /dev/hdb   Size=153G
 Pos MBRPos Type/Name  Size Active Hide  Start Block    Blocks
 --- ------ ---------- ---- ------ ---- ------------ ------------
  No partitions found on this disk

I don't know why it is showing a disk 5, I as I don't have 6 disk in the PC.  After that I did the following:

ubuntu@ubuntu:/tmp$ sudo fdisk -l

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1           5       40131   83  Linux
/dev/hda2               6         193     1510110   82  Linux swap / Solaris
/dev/hda3             194       12643   100004625   83  Linux

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14946   120053713+  83  Linux

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30515   245111706   83  Linux

ubuntu@ubuntu:/tmp$ sudo mount -t reiserfs -o rw /dev/hda3 /mnt
ubuntu@ubuntu:/tmp$ sudo chroot /mnt
root@ubuntu:/# cd /
root@ubuntu:/# cd /boot
root@ubuntu:/boot# ls
root@ubuntu:/boot# ls -la
total 1
root@ubuntu:/boot# sudo grub-install /dev/hda
Probing devices to guess BIOS drives. This may take a long time.
The file /boot/grub/stage2 not read correctly.
root@ubuntu:/boot# 

I unmounted / and looked in the /boot/grub directory and this is what is there:

root@ubuntu:/boot/grub# ls
default     e2fs_stage1_5  jfs_stage1_5    reiserfs_stage1_5  stage2
device.map  fat_stage1_5   minix_stage1_5  stage1             xfs_stage1_5
root@ubuntu:/boot/grub# cat device.map
(fd0)   /dev/fd0
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
(hd3)   /dev/sdc
(hd4)   /dev/sdd

I'm not really sure what in the world I should even be doing at this point.  I feel like I'm just going in circles trying the same thing over again expecting different results... in other words I feel like I'm retarded or insane.  I would really appreciate any input.

Thanks,
mleman

---

### Post by longlegs on 2007-07-13
Hi !
Regarding your question about why is it showing 6 drives. It isn't. 
(hdX,Y) indicates X as drive number starting with 1, not 0, so (hd5,Y) is pointing at the 5th drive, not 6th. HOWEVER (hdX,5) IS pointing at the 6th partition as partitions are numbered 0 to Pcount-1.
Another way of saying this is that drives are counted 1 to drive count and partitions are 0 to partition count.-1
Good Luck
longlegs

---

