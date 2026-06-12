---
title: "how to instal 11.04 on external ONLY"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by blitzkriegg9x on 2011-05-09
i would like to instal Ubuntu 11.04 on my external hard drive only. and leave my internal alone. i would still like to be able to boot up in 11.04 and win 7 (whatever i choose)

but im rather new to this and don't know how and don't want to mess something up. I have tried to use Ubuntu in the past but i just couldn't get the hang of it and messed a lot of things up and just gave up, but i want to try again. 

im a noob so try and explain things. thank you!

my specs:

[IMG]http://i55.tinypic.com/1zqbgxz.png[/IMG]

---

### Post by oldfred on 2011-05-09
I prefer to partition in advance and use manual install. In fact to be able to install grub2's boot loader to the MBR of the external you have to use manual  install. Then set BIOS to boot external first. If not found then it will boot the internal drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

With nVidia you may have video issues. It just needs nomodeset on liveCD and first boot. 11.04 was better than older versions so it may work without the nomodeset.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by blitzkriegg9x on 2011-05-09
can you recommend a good way to partition my external hard drive? and do i need to do anything "special" while doing so?

---

### Post by oldfred on 2011-05-09
Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

How big is drive. Are you sharing data with windows? If so I like a shared NTFS partition for any data you may want to share. Are you thinking about other installs, or even another copy of Ubuntu?

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by blitzkriegg9x on 2011-05-09
i have a blank 500 gb external hard drive but i would like to use some of that to store files from windows and ubuntu like music and pictures ect ect.  and htat he part i dont get ill take a look at your links but im still not exactly sure what to do

i get the point ware i have to tell it what partition to instal on, and i have my blank 500 gb hard drive and i make a new partition and i dont know what to make it because don't know what all that is. i forget what exactly it was but there was "/home and / and a few other things that begun with /" and i dont know witch one to pick

---

### Post by bcschmerker on 2011-05-09
> **oldfred said:**
> ...With nVidia you may have video issues. It just needs nomodeset on liveCD and first boot. 11.04 was better than older versions so it may work without the nomodeset....

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)Thanks for the tip on boot parameters.  I am currently rebuilding an eMachines®/Acer® EL1210-09 (Advance Micro Devices® Athlon® 64 LE-1620, nVIDIA® MCP78S integrated chipset/GeForce® 8200 GPU) with a new Shuttle® PC6300002 PSU and 4 GB RAM, and plan on doing my initial tests from the 11.04 Natty AMD64 Live/Install DVD (using the stock LG® LabelFlash®-equipped optical drive).  Further advice can be posted to my Thread "[ Caveats for Acer slimlines with nVIDIA GeForce 8200 IGP](http://ubuntuforums.org/showthread.php?t=1749981) in [General Help](http://ubuntuforums.org/forumdisplay.php?f=331).

(I previously had a problem with uncommanded shutdowns with an Elitegroup® mobo using the same chipset and an AMD® Athlon® X2 5600+; but the stock BIOS thereof proved the prime suspect of these shutdowns, as several manufacturers, incl. Elitegroup Computer Systems, use a Microsoft® DSDT compiler specifically set up for Windows® 6-up, viz., Vista/SP1/SP2, Server 2008/R2, and Se7en.)

---

### Post by oldfred on 2011-05-10
My post above has mount points and suggested sizes for everything but /home. You do not want to create any of the other system folders as partitions, just / (root), /home  & swap.

If you are planning on putting most of your data into a shared NTFS partition, your /home does not have to be large. The actual data (mostly hidden) that is your user settings is less than 1GB all the rest is for you to store your data. Only you can decide what data you may want in /home as you will not want it in windows or want to save in the shared NTFS. My shared was originally 20GB and when I rebuilt computer I made it 50GB but do not use it much as now almost all my data is just for Ubuntu and I use XP very little. But I still have my Firefox & Thunderbird profiles in the NTFS as I have yet to move them to my data partition.

You also do not have to partition the entire drive immediately. Just be sure to leave any unallocated next to the extended partition as you will have to expand the extended partition to use the unallocated space for more logical partitions.

---

### Post by ledzepjes on 2011-05-10
[LEFT]As hard drives go, partitions are independent of the operation system, windows, linux, it doesn't matter, you can only have four primary partitions, or three primary and one extended. The hard drive considers the extended partition a primary partition but it allows you to make more than four inside the extended partition, you can create almost as many as you want, I forget the limit but it's pretty high. Inside the Extended partition, partitions are called Logical partitions.

What I usually do, is make:
1) one NTFS 40gig-60gig primary(windows xp or 7)
2) then a second NTFS 40gig-60gig (windows 7) primary
3) and a third 40gig-60gig blank space (it's a good idea to leave room for copying or moving partitions later)
4) and after the blank space make the fourth space an extended partition. I would put a 40-60gig Logical EXT4 linux partition inside the beginning of the extended partition and just after that create a swap space equal in size to your memory (only need 512mb or 1gig swap to use Ubuntu funtionally but unless your swap is atleast equal size to your memory you won't be able to use sleep mode)
5)and the rest of the drive can be a Logical partition formatted to NTFS for data.

|<-50G-NTFS->|<-50G-NTFS>|<---50G--->|{|<-50G-EXT4->|<---6G--->|<-data-NTFS->|}
|<Primary---->|<Primary---->|<blank---->|{|<Logical------>|<swap--->|<Logical------>|}

Even then, you probably don't need the first primary, and could get by with one primary and one blank space then the extended after that to save more room for a bigger Logical Data partition at the end.

|<-50G-NTFS>|<---50G--->|{|<-50G-EXT4->|<---6G--->|<-data-NTFS->|}
|<Primary--->|<blank----->|{|<Logical----->|<swap---->|<Logical------>|}

The only partitions you need for linux, if you are going to manually partition (which is what I always do) using the program Gparted using a livecd of ubuntu is:
1) an "EXT4" partition (called "/" or root, were Ubuntu gets installed)
2) and a "swap" partition

I would not recommend using any more partitions like "/home", "/data", because anything beyond "/" and "swap" become very complicated later on, especially when upgrading and things, I've lost permissions to the "/home" partition once because I didn't know what I was doing.

Also remember, after using Gparted that you shouldn't use Windows 7 to extend, delete or shrink partitions. After creating the partitions using Gparted, you can install Windows 7 onto the created NTFS partitions, but Windows 7 manipulates partitions differently than Gparted, and I've used Windows 7 to shrink itself and delete partitions before, created with Gparted, and it completely wiped out the Windows 7 partition AND the partition after it, I had to use Testdisk to get them back, took day and half. Just use Gparted to manipulate the hard drive structure later on, and it'll work safely. Windows doesn't work well with Linux, or Gparted, as a general rule of thumb, but you can use Gparted and Windows won't care.
[/LEFT]

---

### Post by bcschmerker on 2011-05-12
> **ledzepjes said:**
> [LEFT]As hard drives go, partitions are independent of the operation system, windows, linux, it doesn't matter, you can only have four primary partitions, or three primary and one extended....

The only partitions you need for linux, if you are going to manually partition (which is what I always do) using the program Gparted using a livecd of ubuntu is:
1) an "EXT4" partition (called "/" or root, were Ubuntu gets installed)
2) and a "swap" partition

I would not recommend using any more partitions like "/home", "/data", because anything beyond "/" and "swap" become very complicated later on, especially when upgrading and things, I've lost permissions to the "/home" partition once because I didn't know what I was doing....
[/LEFT]:lol: Actually, to my knowledge LinUX doesn't even have a primary subdirectory /data.  The chain of root directory and primary subdirectories for Ubuntu® is actually: 

/ (Root Directory), /bin, /boot, /dev, /etc, /home, /lib, /lost+found, /media, /mnt, /opt, /proc, /root, /sbin, /selinux, /srv, /sys, /tmp, 
/usr, /var

Of these, /boot, /home, /opt, /tmp, /usr and /var *can* be split off to dedicated partitions when using a multiple-HDD installation similar to what I am planning for my Everex® TC2502-based hybrid (now packing a Gigabyte® MA78GM-S2HP with all-AMD® CPU/chipset/video); /home ye'll **definitely** want on its own partition, so that a System-partition crash doesn't take out your documents along with the programs.  The swap space needs its own partition, as well.

---

### Post by oldfred on 2011-05-12
Because hard drives do fail, I like to keep a complete bootable system on each hard drive and scatter data and backups about on different drives. 

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

For standard desktops simple configuration makes sense. Only with servers, RAID or LVM where specific applications or uses may then need different partitions for certain parts of the system.

---

### Post by pritam_par on 2011-07-20
Installation on external hard disk is same is installing as internal hard disk. Only thing you have to do is plug in the hard disk while booting from the Ubuntu CD and select the hard disk partition as the root drive for Ubuntu.

---

