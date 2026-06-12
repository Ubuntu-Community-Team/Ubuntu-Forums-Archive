---
title: "GRUB loading...ERROR 22"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by blaster_bolt on 2005-07-04
hi all. i'm a total newb to this linux thing.  i had a 15 gig partition which had ubuntu on. but last night on my 60Gig XP pro parition, i installed virtual pc and installed ubuntu on it. then using the window's computer management, i deleted the guts of the partition. 

anyway this morning when i turn on the machine, it gave me this message, "GRUB loading please wait..." "ERROR 22" and it stays there for the longest time. 

i have no clue what i'm suppoesed to do. please help me.

---

### Post by brim4brim on 2005-07-04
This happened to me.  If you don't have anything important in Ubuntu then just stick in the original CD and reinstall it formatting the parition.

As far as I know Grub needs Linux to work so if your Ubuntu partition is fried it won't work but then I'm pretty new to Linux aswell.

---

### Post by blaster_bolt on 2005-07-04
i actually tried that. with the downloaded "install" CD. but nothing happened. i no longer have an Ubuntu partition. i only what's left of Ubuntu partition, which is nothing. because via window's computer management, i deleted the Ubuntu partition. but i "think" the partition is still there, but with no guts. either way, i don't want ubuntu in a separate partition. i have virtual pc, so i want to install Ubuntu in my window's partition using virtual pc.

---

### Post by brim4brim on 2005-07-04
[QUOTE=blaster_bolt]i actually tried that. with the downloaded "install" CD. but nothing happened. i no longer have an Ubuntu partition. i only what's left of Ubuntu partition, which is nothing. because via window's computer management, i deleted the Ubuntu partition. but i "think" the partition is still there, but with no guts. either way, i don't want ubuntu in a separate partition. i have virtual pc, so i want to install Ubuntu in my window's partition using virtual pc.[/QUOTE]

You could install it for now to get windows working on a new temp partition just big enough for Ubuntu.  At the end of installation it would prepare and reinstall Grub for you.  Then work on sorting out the rest or your problems from there.

---

### Post by mingus on 2005-07-04
[QUOTE=blaster_bolt]
anyway this morning when i turn on the machine, it gave me this message, "GRUB loading please wait..." "ERROR 22" and it stays there for the longest time. 
[/QUOTE]

This error occurs when grub is pointed to a partition that does not exist - which is the case, since you got rid of it.  So you previously installed grub to the computer's MBR?

If so, use the XP install media to enter the Recovery console and at the command prompt type >fixmbr.

---

### Post by WildTangent on 2005-07-04
i can show you how to restore the windows boot loader to fix XP. what you need to do is get the disk you installed XP with (it has to be the same version and service pack) and boot it, when it gives you a menu, type R to repair windows. it will ask you what windows installation you want to repair, itll list them (if you have more than one, but ill assume you dont), just press 1 and then enter. if you have an administrator password, youll have to enter it now. now youll have a command prompt, type "fixmbr" without the quotes, itll say something about this could damage your partition table (and it may, but its EXTREMELY unlikely, in any case, i will not be held responsible) type "y" and then hit enter and its done. type "exit" and take the cd out, your computer is now rebooting

-Wild

---

### Post by mingus on 2005-07-04
BTW, if you do not have XP (or W2K) install media (a manufacturer's recovery CD will not work), this can also be done with a W98/ME/DOS bootable diskette (which you can get at bootdisk.com).  The command is >fdisk /mbr

---

### Post by blaster_bolt on 2005-07-04
thanks guys.i'll work on it after i get back from work. i'll report what happened for sure.

---

### Post by blaster_bolt on 2005-07-05
hey mingus thanks for your kind reply :) . i did go to bootdisk.com and found this [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) well honestly i have no clue which to download... please help me :|

---

### Post by mingus on 2005-07-05
[QUOTE=blaster_bolt]hey mingus thanks for your kind reply :) . i did go to bootdisk.com and found this [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) well honestly i have no clue which to download... please help me :|[/QUOTE]

I suggest downloading 3:  The DOS 6.22, W98 OEM, and W98 Custom.  You will of course need to be in a working system to do this.  Each download is an executable; just double-click on it and it will unpack the file and write it to a diskette.  I would try the W98 OEM version first.  The W98 Custom use only if the other cannot initialize a ramdisk.  Use the DOS vsn if the other 2 don't work (it's Caldera).  When you've booted, just be sure you are at the A:\ prompt.  Then do >fdisk /mbr

---

### Post by blaster_bolt on 2005-07-05
ok so i tried both 98 se and se custom, and dos version. but none of them read the Harddrive size right. added to that, i couldn't even make a new partition nor delete one. either because the partition was full or there's no "deletable" partition...darn i'm pissed...

---

### Post by mingus on 2005-07-05
*ok so i tried both 98 se and se custom, and dos version. but none of them read the Harddrive size right*

Did you actually try to install the MBR with >fdisk /mbr?  And, what is the total drive size?  In the BIOS setup, is the full capacity recognized?  What was the capacity shown from the floppy FDISK?  Do you have the drive set to LBA?

*then using the window's computer management, i deleted the guts of the partition . . . i only what's left of Ubuntu partition, which is nothing. because via window's computer management, i deleted the Ubuntu partition. but i "think" the partition is still there, but with no guts.*

How did you delete the "guts" but not the partition itself?  What makes you think it is still there?

*i couldn't even make a new partition nor delete one. either because the partition was full or there's no "deletable" partition...*

Were you trying to do this from the diskette?  Why do you say there's no deletable partition?

*darn i'm pissed...*

Of course.

---

### Post by amrith on 2008-03-22
I am facing the same issue ( Now I am typing this through the LIVE CD ) :confused:

I had created a new partition of 4 GB of ext3 after which I rebooted At that time the it displayed ERROR 15 .
Using Live CD I removed the newly created partition and now it shows ERROR 22 .

Please help me as I dont want to lose ubuntu or windows either .
Please please , !!!

---

### Post by confused57 on 2008-03-22
> **amrith said:**
> I am facing the same issue ( Now I am typing this through the LIVE CD ) :confused:

I had created a new partition of 4 GB of ext3 after which I rebooted At that time the it displayed ERROR 15 .
Using Live CD I removed the newly created partition and now it shows ERROR 22 .

Please help me as I dont want to lose ubuntu or windows either .
Please please , !!!
Open a terminal and post the output of:
```
sudo fdisk -l
```
-l is a small "L"

---

### Post by amrith on 2008-03-22
This is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16d916d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3825    30724281    7  HPFS/NTFS
/dev/sda2   *        3826        7649    30716280    7  HPFS/NTFS
/dev/sda3            7650       11473    30716280    7  HPFS/NTFS
/dev/sda4           11474       26995   124680465    f  W95 Ext'd (LBA)
/dev/sda5           11474       16572    40957686    7  HPFS/NTFS
/dev/sda6           16573       21671    40957686    7  HPFS/NTFS
/dev/sda7           21672       25495    30716248+   7  HPFS/NTFS
/dev/sda8           26133       26861     5855661   83  Linux
/dev/sda9           26862       26983      979933+  82  Linux swap / Solaris
/dev/sda10          26984       26995       96358+  83  Linux
ubuntu@ubuntu:~$

---

### Post by confused57 on 2008-03-22
If /dev/sda8 is your linux partition, try mounting it from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda8 /media/ubuntu
```
then post the boot entries in your menu.lst:
```
gedit /media/ubuntu/boot/grub/menu.lst
```

---

### Post by amrith on 2008-03-22
Thats right /dev/sda8 is my partition.

I successfully did this:

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda8 /media/ubuntu

But when I do this:
ubuntu@ubuntu:~$ gedit /media/ubuntu/boot/grub/menu.lst

The file is blank !

And also i notice the folder doest exist "error accessing 'file:///media/ubuntu/boot/grub': File not found"

---

### Post by confused57 on 2008-03-22
Do you get a grub boot menu when you boot your computer?  If you do, try highlighting your Ubuntu entry, press "e", then highlight the line with root(it should have hd0,7), if it doesn't press "e" again, then change root to (hd0,7), press "enter", then "b" to boot.

Exactly how did you repartition your drive, i.e. which partition did you resize or anything else you think of that might help.

Here's a description of grub error 22:
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

If you have access to another computer, you might try Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

While you're booted in the live cd, try reinstalling grub to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
note any error messages, if it doesn't work and where /find/boot/grub/stage1 shows your root partition.

---

### Post by amrith on 2008-03-22
I do not get the GRUB bot menu.

Its says " GRUB loading...ERROR 22 " and halts there.

There was a FAT32 partition at I guess /dev/sda8 which I wanted to use for linux purpose So I deleted the partition in Windows and the booted with sysresccd ,then using GParted I formatted to ext3 later I got ERROR 15 then I booted to Live CD and removed the partition.

Does the above info help anything ? :confused:

---

### Post by amrith on 2008-03-22
[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub>

---

### Post by confused57 on 2008-03-22
> **amrith said:**
> I do not get the GRUB bot menu.

Its says " GRUB loading...ERROR 22 " and halts there.

There was a FAT32 partition at I guess /dev/sda8 which I wanted to use for linux purpose So I deleted the partition in Windows and the booted with sysresccd ,then using GParted I formatted to ext3 later I got ERROR 15 then I booted to Live CD and removed the partition.

Does the above info help anything ? :confused:
Try reinstalling grub to the mbr, using the live cd.

You can also see if grub can find your root partition:
```
sudo grub
find /sbin/init
quit
```

If grub doesn't find a root partition, it's possible your root partition was overwritten when you were partitioning

You might look into using Testdisk to possibly recover your filesystem?:
[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)
I've never used Testdisk, but this link has some excellent instructions.

If you want to reinstall your Windows IPL to the mbr so you can boot Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Added:  Just to see what's on /dev/sda8, you can mount it, then
```
cd /media/ubuntu
ls -la
```

---

### Post by amrith on 2008-03-22
I tried doing the said stuff in the other link u gave :

These are what I got :


grub> find /sbin/init
 (hd0,7)

grub> setup (hd0,7)

Error 12: Invalid device requested

grub> setup (hd0)

Error 12: Invalid device requested

grub> root (hd0,7)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 

-----------------------------------------------
I have managed to get my old menu,lst in my sent items in gmail.Will that be useful .Can I manually save that file ?

---

### Post by amrith on 2008-03-22
ubuntu@ubuntu:~$ cd /media/ubuntu
ubuntu@ubuntu:/media/ubuntu$ ls -la
total 116
drwxr-xr-x  23 root root  4096 2008-03-21 13:44 .
drwxr-xr-x   3 root root    60 2008-03-22 06:57 ..
drwxr-xr-x   2 root root  4096 2008-03-21 08:57 2.6.18-1.2849.fc6
drwxr-xr-x   2 root root  4096 2008-03-21 13:44 afs
drwxr-xr-x   2 root root  4096 2008-02-03 11:25 bin
drwxr-xr-x   2 root root  4096 2008-02-03 10:53 boot
lrwxrwxrwx   1 root root    11 2008-02-03 10:53 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2007-10-15 23:28 dev
drwxr-xr-x 122 root root 12288 2008-03-22 05:29 etc
drwxr-xr-x   6 root root  4096 2008-03-09 12:35 home
drwxr-xr-x   2 root root  4096 2007-10-15 23:17 initrd
lrwxrwxrwx   1 root root    33 2008-02-03 11:24 initrd.img -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root 12288 2008-03-01 07:05 lib
drwx------   2 root root 16384 2008-02-03 10:53 lost+found
drwxr-xr-x  10 root root  4096 2008-02-10 09:28 media
drwxr-xr-x   2 root root  4096 2007-10-08 10:47 mnt
drwxr-xr-x   2 root root  4096 2007-10-15 23:17 opt
drwxr-xr-x   2 root root  4096 2007-10-08 10:47 proc
drwxr-xr-x  18 root root  4096 2008-03-21 09:10 root
drwxr-xr-x   2 root root  4096 2008-03-21 13:44 sbin
drwxr-xr-x   2 root root  4096 2007-10-15 23:17 srv
drwxr-xr-x   2 root root  4096 2007-10-04 11:17 sys
drwxrwxrwt  12 root root  4096 2008-03-22 05:26 tmp
drwxr-xr-x  12 root root  4096 2008-02-15 17:50 usr
drwxr-xr-x  15 root root  4096 2007-10-15 23:31 var
lrwxrwxrwx   1 root root    30 2008-02-03 11:24 vmlinuz -> boot/vmlinuz-2.6.22-14-generic
ubuntu@ubuntu:/media/ubuntu$

---

### Post by confused57 on 2008-03-22
Looks like your filesystem is on /dev/sda8, but your former menu.lst is showing /dev/sda11((hd0,10).  I'm not really sure what you need to do, unless someone else has a better suggestion, you could try chrooting into /dev/sda8 & try reinstalling grub:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda8 /media/ubuntu
sudo mount -t proc none /media/ubuntu/proc
sudo mount -o bind /dev /media/ubuntu/dev
sudo chroot /media/ubuntu /bin/bash
sudo apt-get install grub
```

This may not work, but you could give it a try.

Have you tried booting the live cd & select "Boot Hard Disk", or something to that effect?

I still believe your best bet would be to get a copy of Super Grub Disk and trying a direct kernel boot.

It's getting late here, so I probably won't be able to help you any more this morning...good luck & maybe Herman or someone else can help you.  I'll check back when I get up to see how it's going.

---

### Post by amrith on 2008-03-22
the commands didnt work..:(

Getting Super Grub - I wish I had another CD ROM to burn it as I am through live CD .

Will wait till somebody else gives a solution else the last option - installing ubuntu again :(

---

### Post by amrith on 2008-03-22
Using TestDisk in Sysrcd I wrote new MBR .Now GRUB doesnt show any error but its booting Windows :(

I guess lost my ubuntu :( :( :( 
](*,)

In Diskmanagement I still see those linux partitions ..
Any way I can still recover ubuntu ??

---

### Post by amrith on 2008-03-22
Anybody there??? :(

---

### Post by Pumalite on 2008-03-22
Reinstall. What Windows are you using?XP? Vista?

---

### Post by amrith on 2008-03-22
Reinstall ?? That shud be the last thing I shud do :( 
Isnt there any way I can recover ubuntu ? 

yup,I am on XP and its still alive .

---

### Post by Pumalite on 2008-03-22
Reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Set Grub to XP's MBR

---

### Post by confused57 on 2008-03-22
> **amrith said:**
> Using TestDisk in Sysrcd I wrote new MBR .Now GRUB doesnt show any error but its booting Windows :(

I guess lost my ubuntu :( :( :( 
](*,)

In Diskmanagement I still see those linux partitions ..
Any way I can still recover ubuntu ??
Are you booting from Windows IPL on the mbr or are you actually booting Windows from grub?  If it's the latter, press "c" at the grub boot menu, then enter:
```
root (hd0,7)
```
press "enter"
```
kernel /vmlinuz root=/dev/sda8
```
press "enter"
```
initrd /initrd.img
```
"enter"
```
boot
```
"enter"

You might be able to recover any data by mounting your Ubuntu partition, copying any files you want to save to a flash drive....then reinstall Ubuntu.

---

### Post by amrith on 2008-03-22
Since I have done something in the MBR it is booting thru Windows IPL on the mbr GRUB doesnt exist at all now ...
Any solutions for that ?.

I guess re-installing is the only way .I am not worried about the data that I will lose but I am concerned about re-installing softwares on ubuntu ( esp the pain in installing vmware and others in ubuntu ) .

---

### Post by amrith on 2008-03-22
I took a day in installing VMware . :(
I just cant imagine I need to do that again :( :(

---

