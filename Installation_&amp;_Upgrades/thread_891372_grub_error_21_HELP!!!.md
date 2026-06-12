---
title: "grub error 21 HELP!!!"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by specgoalie717 on 2008-08-16
hey I just got a new Seagate 500Gb SATA HD.  I "installed" it fine using Windows XP.  I then restarted the computer to install the latest Ubuntu from CD.  as it started up I hit F12 to go to the boot menu thingy.  i selected boot from CD.  I hit install.  I went through the steps. I assigned about 150gb of what I assumed was my 500gb HD b/c there was about a 460gb range.  I continued the steps.  and finished it.  It finished up and told me to restart.  I hit the button thus doing so.  

    when it restarted I hit F12 again assuming there would be an option for Ubuntu. I hit the second option being to boot from hard disk assuming it would be under there.  I instead got a message along the lines of "grub loading..." *next line* "error 21." It then did nothing, or froze or whatever.  I then decided to reboot into windows to try to fix it all.  I hit the button on my tower to turn it off.  waited a few seconds turned it back on and DIDN't hit anything.  it still displayed the "error 21" page.  I turned the computer off. I opened up the computer and took out the 500 Gb hard drive.  closed the PC.  turned it on.  same problem.  I turned it off.  put HD back.  closed PC. turned it on.  same problem.  turned it off.  turned it on.  hit F12.  hit the normal button.  same problem.  I got really stressed out.  I put in my live CD of Ubuntu.  ran fine. and am able to access my regular (XP) hard drive.  I checked the Ubuntu Partition Editor and it showed that 3 and a half GB were used of my 150 gb partition for ubuntu on the 500 Gb harddrive.  some other partition that I don't exactly know about takes up the rest of the 500 HD.  

I have tried many sites for help but they are still able to access their regular OS.  

Pleezzee help me I need this computer for school in a few days (the 18th!)

I am pretty decent with computer skills.  

Thank you soooo much, in advance.

---

### Post by confused57 on 2008-08-16
Here is a description & possible solutions of grub error 21:
[http://users.bigpond.net.au/hermanzone/p15.htm#21](http://users.bigpond.net.au/hermanzone/p15.htm#21)

Also, boot the live cd, open a terminal(Applications---Accessories---Terminal) and post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

---

### Post by specgoalie717 on 2008-08-16
hmmm I tried reading that site and all I could muster out of it was possibly a simple fact that the cord isn't all the way in.  but that is strange b/c I can access my original HD's stuff from the live CD.  I'll try triple checking it.  The site didn't make tooo much sense I am not very experienced in this area of computers.  

I tried your "terminal" thing and the code and I got a bunch of stuff that looked like partition info but I couldn't do anything with it or make any since of it.  

please I still need help from anyone out there.

thank you though.

---

### Post by coldbluesteel on 2008-08-16
Error 21 means that grub is looking at the wrong HDD.

Pause grub during the boot process and verify that it is attempting to load from the correct drive.

CBS

---

### Post by confused57 on 2008-08-16
> **specgoalie717 said:**
> hmmm I tried reading that site and all I could muster out of it was possibly a simple fact that the cord isn't all the way in.  but that is strange b/c I can access my original HD's stuff from the live CD.  I'll try triple checking it.  The site didn't make tooo much sense I am not very experienced in this area of computers.  

I tried your "terminal" thing and the code and I got a bunch of stuff that looked like partition info but I couldn't do anything with it or make any since of it.  

please I still need help from anyone out there.

thank you though.
It would really help if you could post the output of "sudo fdisk -l", which shows your drives and the partitions on each drive.
This information should help someone show you how to mount your Ubuntu root partition from the live cd, then you can examine your /boot/grub/menu.lst to see if Ubuntu is trying to boot from the wrong HD, as coldbluesteel mentioned.

---

### Post by specgoalie717 on 2008-08-16
> **confused57 said:**
> It would really help if you could post the output of "sudo fdisk -l", which shows your drives and the partitions on each drive.
This information should help someone show you how to mount your Ubuntu root partition from the live cd, then you can examine your /boot/grub/menu.lst to see if Ubuntu is trying to boot from the wrong HD, as coldbluesteel mentioned.

Hey this is what I wrote but very shortly i'll put up the info from sudo fdisk-1 shortly.



how do I do that? I don't even get that grub menu I think I've heard about.  It just says Loading Grub 1.5. and then it says error 21. I went to the partition editor in the Live CD and just looked at the stuff and everything seemed normal a 465 GB (500gb) harddrive with a large 310Gb /dev/sdb1 ntfs filesytem partition and a 148Gb /dev/sdb5 ext 3 partition with 3.2 Gb used (OS right?).  The only things that seemed out of place were a 6Gb /dev/sdb6partition with a filesystem of Linux-swap.  and the fact that the ext3 and the linux-swap partitions were grouped together under /dev/sdb2.  They were like a "dropdown" partition under sdb2 I guess.

The other hard drive (original) seemed normal like when I checked it out from my XP computer manager program thingy.  It had a 50 Mb /dev/sda1/ fat16 partition.  I don't know what it's for but the Properties said it was unmounted.  I then have a 144 Gb /dev/sda2 ntfs partition.  97Gb used.  mountpoint: /media/disk-1This has gotta be my XP partition. I then have 7Mb unallocated "partition".  There is no "/dev/sda*" thingy.  nor is there a filesystem.  Then I have a 4.6 Gb /dev/sda3 fat 32 partition.  I don't know what is in it though.  

after researching some it seems like boot stage 1 (or is it 1.5)idk) can't find boot stage 2.  idk.  please correct me if wrong.  or just simply help me Pleaseee. 

thank you very much.

---

### Post by specgoalie717 on 2008-08-16
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       18845   151316235    7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe64ef4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       40544   325669648+   7  HPFS/NTFS
/dev/sdb2           40545       60801   162714352+   5  Extended
/dev/sdb5           40545       59974   156071443+  83  Linux
/dev/sdb6           59975       60801     6642846   82  Linux swap / Solaris
 


This is an exact copy of the sudo fdisk -l thingy.  I'm not sure how to interpret it though.  please help. and again THANK YOU!!

---

### Post by specgoalie717 on 2008-08-16
btw, what's strange is that Ubuntu under Places recognizes a 154 GB drive (XP stuff) and a 159 GB drive.  which has random stuff in it idk.  but the weird part is I have no partition that size I have a 144Gb partition for Ubuntu but is that it?!??

---

### Post by confused57 on 2008-08-17
> **specgoalie717 said:**
> Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       18845   151316235    7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe64ef4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       40544   325669648+   7  HPFS/NTFS
/dev/sdb2           40545       60801   162714352+   5  Extended
/dev/sdb5           40545       59974   156071443+  83  Linux
/dev/sdb6           59975       60801     6642846   82  Linux swap / Solaris
 


This is an exact copy of the sudo fdisk -l thingy.  I'm not sure how to interpret it though.  please help. and again THANK YOU!!

First thing I would suggest is to go into your bios setup and check the settings for your hard drive controllers & how bios is recognizing your drives.  I have a Dell that I added a 2nd IDE drive, but the primary IDE slave drive controller setting was "off", changing it to "auto" cleared the error 21 I was getting.
The settings will be different for SATA, but would be worth checking.

If this doesn't work, boot up the live cd, and from a terminal mount your Ubuntu root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb5 /media/ubuntu
```
This should mount your root partition(sdb5) in the /media/ubuntu directory.  Then post your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
menu.lst is short for menu.list...you can probably just post the lower portion with your Ubuntu & Windows boot entries.

If you want to restore your Window's IPL to the first drive's mbr, here are several ways to do so:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
This will at least enable you to boot into Windows for now.

---

### Post by specgoalie717 on 2008-08-17
> **confused57 said:**
> First thing I would suggest is to go into your bios setup and check the settings for your hard drive controllers & how bios is recognizing your drives.  I have a Dell that I added a 2nd IDE drive, but the primary IDE slave drive controller setting was "off", changing it to "auto" cleared the error 21 I was getting.
The settings will be different for SATA, but would be worth checking.

If this doesn't work, boot up the live cd, and from a terminal mount your Ubuntu root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdb5 /media/ubuntu
```
This should mount your root partition(sdb5) in the /media/ubuntu directory.  Then post your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```
menu.lst is short for menu.list...you can probably just post the lower portion with your Ubuntu & Windows boot entries.

If you want to restore your Window's IPL to the first drive's mbr, here are several ways to do so:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
This will at least enable you to boot into Windows for now.
Hey Thank you very much!! you seem to know what you are talking about.  but could you possibly be a little more detailed in your instructions like a step-by-step or at least tell me where to find this stuff.  Please, I can not thank you enough for your help!!

---

### Post by confused57 on 2008-08-18
To restore use of your computer, I would recommend trying to restore your Windows IPL(Initial Program Loader) to the mbr of the first drive.  If you have a Windows install cd(not a recovery disk), boot up your pc with the disk inserted in your cd drive, press "r", then enter "fixmbr", without the quotes.

If you don't have a Windows install cd and have access to another pc, you can download & burn a copy of Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
download the SGD .iso, burn it to cd as an "image", not as a data or bootable cd...then boot up your pc with SGD inserted, and find the option "Fix Boot of Windows".

Another method that I'm not familiar with is ms-sys, using the Ubuntu live cd:
[http://ubuntuforums.org/showpost.php?p=5046817&postcount=326](http://ubuntuforums.org/showpost.php?p=5046817&postcount=326)

This  should restore use of your computer, then you can try reinstalling Ubuntu at a later time.  Here's a tutorial that you might try:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

When I was first starting with Ubuntu & Linux, I would have to read Linux guides several times & still just have a vague idea of what I just read, so I can understand your difficulty with understanding any guides related to Linux.

Good Luck

---

