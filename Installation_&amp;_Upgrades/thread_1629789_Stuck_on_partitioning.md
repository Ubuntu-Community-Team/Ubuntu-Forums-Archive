---
title: "Stuck on partitioning"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by 1/0 on 2010-11-24
I'm trying to install Maverick on my computer (not upgrade). I have 3 hd:s but for simplicity I've removed all but my new 2 Tb WD HD SATA. The install freezes on partitioning.

I tried Knoppix and gparted same same. That is,  Gparted will not even start on the Ubuntu live CD. ctrl+shift+alt+sysrq+r+e+i+s+u+b doesn't work, no mouse, no keyboard.

fdisk says that there's some gparted partition that it can't handle. When I ignore the message and delete the partition, repartion the drive it's fine until I run mkfs.ext4 in term. It freezes on table 2181/14741. 

Anyway, I'm stuck so an ideas or help is much appreciated.

---

### Post by srs5694 on 2010-11-24
To the best of my knowledge, fdisk never complains about a "gparted partition," although it does mention GParted in some situations, such as when it detect a GUID Partition Table (GPT). I recommend you post the output of typing "sudo fdisk -lu". Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

### Post by Zookalicious on 2010-11-24
Since you said this was a drive that you are doing a clean install I would suggest either:

A) Downloading and burning a GParted LiveCD (not off of the Ubuntu LiveCD) and booting with that to format the disk

or

B) If you have access to a friends computer and a USB - SATA adaptor, try formatting the disk on other operating systems (except apple, cause guid will screw things up)

or lastly as a last resort

C) You could try downloading and burning a DBan liveCD. This will completely wipe the drive, but even a single pass on a 1TB drive will take hours.

---

### Post by 1/0 on 2010-11-25
I tried gparted, no success. I don't have access to windows that easy so... 

I read somewhere that they changed the sector size to 4096 b (instead of 512 b). Could it be related to that??

The drive I have is a wd20ears.

---

### Post by dino99 on 2010-11-25
as its a 2 Tb hdd you need to set bios on "ahci" or better on "compatible"

large hdd as yours: [http://forums.penny-arcade.com/showthread.php?t=113313](http://forums.penny-arcade.com/showthread.php?t=113313)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by 1/0 on 2010-11-25
> **dino99 said:**
> as its a 2 Tb hdd you need to set bios on "ahci" or better on "compatible"

large hdd as yours: [http://forums.penny-arcade.com/showthread.php?t=113313](http://forums.penny-arcade.com/showthread.php?t=113313)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

I changed in bios from disabled (i.e. SATA shows as PATA under IDE) to AHCI. I ran the alternative livecd and it crashes on partitioning. This seems weired to me, as I thought GNU/Linux didn't use bios at all. 

Before this I fiddled around and managed to partition the drive but it instead crashed after partitioning. Error message: "The installer encountered an error copying files to the hard disk"...

---

### Post by 1/0 on 2010-11-25
> **srs5694 said:**
> To the best of my knowledge, fdisk never complains about a "gparted partition," although it does mention GParted in some situations, such as when it detect a GUID Partition Table (GPT). I recommend you post the output of typing "sudo fdisk -lu". Please post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

You're right it said GPT and not gparted. 

Here's the result of the fdisk:

```

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sdb

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c93c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     4401151     2199552   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb3         4401810    45367559    20482875   83  Linux
/dev/sdb4        45369342  1953520064   954075361+   5  Extended
/dev/sdb5        45369344   147763199    51196928   83  Linux
/dev/sdb6       147765933  1953520064   902877066   83  Linux


```

Oh and btw, this time I tried with other cylinders, hence the message on sdb1

---

### Post by srs5694 on 2010-11-25
Some comments, observations, and suggestions:


[list]
[*]Your current partition table looks fine to me (as in there are no obvious errors).
[*]Linux doesn't use the BIOS for most purposes once booted, but the BIOS still sets up the hardware and begins the boot process; thus, Linux does rely on the BIOS and BIOS settings can be very important to Linux.
[*]The WD20EARS drive uses 4096-byte sectors, but it presents the illusion of 512-byte sectors to the computer. Linux works fine with these drives, although there are caveats about partition alignment. Read about them [in this article I wrote,](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) among other places. These issues should not be causing GParted or any installer to crash.
[*]Try running the text-mode GNU Parted on the disk ("sudo parted"). It might present some error messages that would be diagnostic.
[*]Try running GParted from the command line ("sudo gparted") rather than launching it via a GUI. It might display error messages in the shell that you won't see when launching it via a GUI.
[*]After an error, type "dmesg | tail" and look for errors relating to the hard disk.
[/list]

---

### Post by 1/0 on 2010-11-25
The problem with gparted is that it really really crahses, i.e. no reisub, no nothing. So, no output available and no dmesg due to the live cd. If I set the option: *SATA AHCI Mode* to *AHCI* gparted crashes. The only other option is *DISABLED* which resolves this problem with gparted crahsing (and also makes DOS see the drive).

Before when it only crashed "a little", as it wouldn't even start, I got the error message: *glibmm-ERROR **: unhandled exception (type std::exception) in signal handler: what: basic_string::_S_create aborting...*

I don't have the option "round to cylinders" in the same menu as in your article. I don't know if it's relevant or not.

As for the BIOS part, sure it's needed to start GRUB, but that shouldn't stop the installation... 

parted is a bit difficult to use. Especially the start point for the second and third partition, since I made the first root partition 15 Gb large and don't know the last cylinder.

---

### Post by b0b138 on 2010-11-25
You said "removed all but my new 2 TB drive..."  Is this a brand new drive you haven't used before?  Maybe the drive is bad.

---

### Post by 1/0 on 2010-11-25
> **b0b138 said:**
> You said "removed all but my new 2 TB drive..."  Is this a brand new drive you haven't used before?  Maybe the drive is bad.

True, but somehow I suspect not since there's more people having problems with large sector drives. It bugs me that the WD test program crashes as well. Otherwise I would have 99% sure answear to that question.

---

### Post by 1/0 on 2010-11-25
I changed back AHCI to disabled in bios which suddenly made the WD test program run. A quick test said the drive is fine. I'm running an extended test that will take more than 2 hours... I suspect that the drive is fine. Hence the problem is with GNU/Linux and most likely that 4096 b sector thingy.

---

### Post by 1/0 on 2010-11-26
I've narroved it down a little. It's when I run mkfs that the largest partition crashes.

---

### Post by srs5694 on 2010-11-26
The problem is not with 4096-byte sectors per se (many people, myself included, use these drives with no problem); however, it's possible that something about that specific model drive is interacting badly with your motherboard's disk controller or the Linux drivers for it. If so, your best bet is to replace the drive. You can't be sure this is the case without trying another drive, though. If you can swap out another drive, even on a temporary test basis, that's a worthwhile test. If another drive works, then you should exchange your new WD drive for another model, since it is essentially defective by design, at least in your computer.

Also, if mkfs is failing, it's conceivable that using a different filesystem will produce better results. If you're using ext3fs or ext4fs, try ReiserFS, XFS, or JFS instead. (I'm not sure which filesystems the installer supports.)

---

### Post by 1/0 on 2010-11-29
> **srs5694 said:**
> The problem is not with 4096-byte sectors per se (many people, myself included, use these drives with no problem); however, it's possible that something about that specific model drive is interacting badly with your motherboard's disk controller or the Linux drivers for it. If so, your best bet is to replace the drive. You can't be sure this is the case without trying another drive, though. If you can swap out another drive, even on a temporary test basis, that's a worthwhile test. If another drive works, then you should exchange your new WD drive for another model, since it is essentially defective by design, at least in your computer.

Also, if mkfs is failing, it's conceivable that using a different filesystem will produce better results. If you're using ext3fs or ext4fs, try ReiserFS, XFS, or JFS instead. (I'm not sure which filesystems the installer supports.)


Thanks for the advice. I changed back to the original drive but I get the same problem! I've got about 5 copies (verified) of ubuntu - all fail. I've tried Debian and Fedora with the same result. I've tried ext3, xfs and reiserfs on these distros with the same outcome. I'm starting to fear that it's the motherboard but why?

---

### Post by 1/0 on 2010-11-29
I was about to buy a new motherboard but I want to rule out all other possibilities first. 

I was able to install XP on the computer, so it's not broke. One of my other drives is a 1 Tb Western Digital WD10EADS. I'm not sure if its also the same sector size. Previously I was able to install on that drive but now I can't install on either of the drives... I've switched cables to rule out any faulty cables (still, XP works). I've tried various distros and drives. They all say that there was a read/write error that is usually due to the CD being borked. I still can't get the computer to boot from the USB stick. I've got options such as USB-FDD, USB-ZIP, USB-CDROM and USB-HDD. They all fail to boot. 

This is really bugging me. Problems are meant to be solved (or removed imo). I really really don't want to go down the Microsoft road. I know where that road ends...

---

### Post by Zookalicious on 2010-11-29
> **1/0 said:**
> This is really bugging me. Problems are meant to be solved (or removed imo). I really really don't want to go down the Microsoft road. I know where that road ends...

If you are using the same installation CD's that used to work in the  past, and now don't, and since you have tried every Linux distro you  own, it is an indication of hardware difficulties, rather than a software problem that cannot be easily "solved or removed". Consider  resetting your BIOS as there might be an error there. Also consider trying to run the installation on a different computer with the same drive, or on the same computer with a different drive if you know someone who will let you borrow their rig for a little bit.

---

### Post by 1/0 on 2010-11-29
It seems more and more hardware related... I can't even install on a PATA drive anymore. This is what I get when installing 10.10:

syslog
```
Nov 29 21:56:25 ubuntu python: Traceback (most recent call last):
Nov 29 21:56:25 ubuntu python:   File "/usr/share/ubiquity/install.py", line 608, in <module>
Nov 29 21:56:25 ubuntu python:     install.run()
Nov 29 21:56:25 ubuntu python:   File "/usr/share/ubiquity/install.py", line 122, in run
Nov 29 21:56:25 ubuntu python:     self.copy_all()
Nov 29 21:56:25 ubuntu python:   File "/usr/share/ubiquity/install.py", line 389, in copy_all
Nov 29 21:56:25 ubuntu python:     self.db.progress('SET', 10 + copy_progress)
Nov 29 21:56:25 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 65, in <lambda>
Nov 29 21:56:25 ubuntu python:     lambda *args, **kw: self.command(command, *args, **kw))
Nov 29 21:56:25 ubuntu python:   File "/usr/lib/python2.6/dist-packages/debconf.py", line 70, in command
Nov 29 21:56:25 ubuntu python:     self.write.flush()
Nov 29 21:56:25 ubuntu python: IOError: [Errno 32] Broken pipe

```

partman
```
parted_server: Partitions printed
parted_server: OUT:


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 371
parted_server: Opening infifo
/lib/partman/finish.d/80parted: *******************************************************
/lib/partman/finish.d/80parted: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting

```

I'll try changing in BIOS and installing Debian next.

---

### Post by 1/0 on 2010-11-30
I managed to install Lenny on the old PATA drive. The installation crashed but I managed to install GRUB and the basic stuff. I was able to install the rest (e.g. xorg) after reboot.

I figured maybe it would work on the other drive as well but no. It crashes installing the base system...

partman:
```
parted_server: OUT: 


parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 549
parted_server: Opening infifo
/lib/partman/finish.d/80parted: *******************************************************
/lib/partman/finish.d/80parted: IN: QUIT
parted_server: Read command: QUIT
parted_server: Quitting

```

syslog:
```
Nov 30 21:32:34 kernel: [ 2477.000139] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Nov 30 21:32:34 kernel: [ 2477.000139] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Nov 30 21:32:34 kernel: [ 2477.370097] sd 6:0:0:0: [sdb] 15687680 512-byte hardware sectors (8032 MB)
Nov 30 21:32:34 kernel: [ 2477.373526] sd 6:0:0:0: [sdb] Write Protect is off
Nov 30 21:32:34 kernel: [ 2477.373529] sd 6:0:0:0: [sdb] Mode Sense: 23 00 00 00
Nov 30 21:32:34 kernel: [ 2477.373531] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Nov 30 21:32:34 kernel: [ 2477.373533]  sdb:
Nov 30 21:32:34 kernel:  sdb1
Nov 30 21:32:34 kernel: [ 2477.400160] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Nov 30 21:33:04 kernel: [ 2509.002622] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```

Btw. The last part of the syslog is probably from inserting the USB stick to save the tail.

---

### Post by wayne128 on 2010-12-01
I read your posts and just think it is more likely mother board is bad.
Sometime, mother board become bad when the electrolytic capacitors leak, dry up and thus power supply becomes noisy hence leading to all kinds of read/write errors.
One thing about this is that it is very random because hardware can no longer operate properly.
May be you want to just check if your mother board has burged caps, like these images on the link. If you have these burged caps you could replace them and usually it cured. 
BY the way I got one like that, it is quite old already, after caps replacement, this old mother board is still working nicely for long time.

[http://www.google.com.sg/images?oe=utf-8&rls=com.pclinuxos:en-US:unofficial&client=firefox-a&q=bulged+capacitor&um=1&ie=UTF-8&source=univ&ei=INj1TK_KFovqrQee0eGiBw&sa=X&oi=image_result_group&ct=title&resnum=1&ved=0CCgQsAQwAA&biw=1300&bih=555](http://www.google.com.sg/images?oe=utf-8&rls=com.pclinuxos:en-US:unofficial&client=firefox-a&q=bulged+capacitor&um=1&ie=UTF-8&source=univ&ei=INj1TK_KFovqrQee0eGiBw&sa=X&oi=image_result_group&ct=title&resnum=1&ved=0CCgQsAQwAA&biw=1300&bih=555)

---

### Post by 1/0 on 2010-12-01
Prior to getting a new drive, I started getting errors on downloaded files. I could, for instance, not decompress rar files. I thought it was the fs on the drive. Hence the new drive.

---

### Post by Zookalicious on 2010-12-02
I think we're all leaning towards the bad motherboard route.

---

### Post by 1/0 on 2010-12-05
I was about to buy a new motherboard but I realized that a faulty RAM could create various problems. In my case one of the sticks had a ton of errors showing up in memtest. I've bought new RAM and I am going to try again, only I managed to partition the wrong drive so now I need some forensics program or something to get the info back...

---

