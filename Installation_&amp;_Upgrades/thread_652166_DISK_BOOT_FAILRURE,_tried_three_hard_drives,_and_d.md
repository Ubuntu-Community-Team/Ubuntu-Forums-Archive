---
title: "DISK BOOT FAILRURE, tried three hard drives, and dozens of installs"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by nicklikesfire on 2007-12-28
Hello.

I'm running an AMD 64 processor, with two 500G SATA hard drives I'm using only for media storage.

I'm trying to install my OS on an IDE hard drive.

I started with gutsy 7.06. This worked fine. I removed this Hard drive, I then tried installing 7.10, gutsy, from a live CD, onto a diffrent IDE hard drive. This did not work. The install fnishes, but when I restart, I get the error "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"

At this point I must restart the computer, with the install CD in, and when I get to the menu on the CD, I can choose the bottom option "boot from first hard disk" and everything works great. I have no idea why this is happening.

When I install I'm using:

ext2, /boot - 131MB
reiserfs, / - 40,000 MB
swap - 8000 MB
xfs, /usr - the rest (100,000+ MB)

I've tried installing using 3 diffrent HD's (maxtor, WD, WD) all with the same result. They have all been set to "master" using the jumper, and are on the master end of the ide cable.

What's worse is that the original HD, with 7.06 on it, now does the same thing. I swapped that back in, and I get the same error message.

Any clues? I'm really new at this, so I'm not good with complicated things yet. I don't want to switch back to windows.

Thanks for all your help

---

### Post by logos34 on 2007-12-28
Boot from the live cd and run this in a terminal:

sudo fdisk -l

Post it.

Sounds like when you tried installing on the other disks grub went the the mbr of one of the sata drives rather than IDE--but the bios is now trying to boot from the other sata which has nothing on the mbr.  Just a guess.

If you could, also post the menu.lst and device.map:

>Place>computer>click on root partition to mount

cat /media/disk/boot/grub/menu.lst /media/disk/boot/grub/device.map

---

### Post by nicklikesfire on 2007-12-28
Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xe1a3bf8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      969021   488386552+  42  SFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xe1a3bf8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      969021   488386552+  42  SFS

Disk /dev/hdc: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60073615

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          16      128488+  83  Linux
/dev/hdc2              17        4988    39937590   83  Linux
/dev/hdc3            4989        5968     7871850   82  Linux swap / Solaris
/dev/hdc4            5969       24792   151203780   83  Linux


I'm not really sure what you mean by:

"If you could, also post the menu.lst and device.map:

>Place>computer>click on root partition to mount

cat /media/disk/boot/grub/menu.lst /media/disk/boot/grub/device.map"

Despite the fact that the two 500 GB SATA disks show up above, I can't even find them on the desktop.

---

### Post by logos34 on 2007-12-28
> **nicklikesfire said:**
> I'm not really sure what you mean by:

"If you could, also post the menu.lst and device.map:

>Place>computer>click on root partition to mount

cat /media/disk/boot/grub/menu.lst /media/disk/boot/grub/device.map"

Despite the fact that the two 500 GB SATA disks show up above, I can't even find them on the desktop.

oops, my mistake...forgot about the separate /boot partition...you would mount hdc1 to get to those files

I'd set the ide first in the Bios hard disk boot priority, then reinstall grub making sure it goes on the mbr of the ide disk.  See if that does anything.  Use [this guide]("http://ubuntuforums.org/showthread.php?t=224351").  You 'root' lines (and 'groot') in menu.lst should read '(hd0,0)'

---

### Post by nicklikesfire on 2007-12-28
Hello,

Ok, so I went here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

And tried the first process:

"Code:

find /boot/grub/stage1"

At this point I cot an error. so I tried the second process.

"
Code:

sudo mkdir /mnt/root

$
Code:

sudo mount -t ext3 /dev/sda6 /mnt/root"
 but this comes with the disclaimer:

"
PLEASE NOTE: My Ubuntu was installed to /dev/sda6. This may not be the same for everyone. /dev/sdaX means it's SCSI/SATA/USB/FireWire drive. And it's partition 6 because I have a weird partitioning scheme in place."



How do I figure out what to put in place of "/dev/sda6"?

Thanks, hopefully this will work out!

---

### Post by Craigus on 2007-12-28
While it's not a satisfying problem-solving approach, you could see if the supergrub boot disk is able to sort it out for you:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by meierfra on 2007-12-28
> find /boot/grub/stage1"

Do 

```
find /grub/stage1
```

---

### Post by logos34 on 2007-12-28
> **meierfra said:**
> Do 

```
find /grub/stage1
```

That would be it.

---

### Post by psusi on 2007-12-28
You need to edit your /boot/grub/devices.map file to reflect the correct bios disk ordering.  By default it assumes that the boot disk (hd0) is /dev/sda, but in your case it is /dev/hdc.  Then reinstall grub with sudo grub-install.

---

### Post by nicklikesfire on 2007-12-29
> **psusi said:**
> You need to edit your /boot/grub/devices.map file to reflect the correct bios disk ordering.  By default it assumes that the boot disk (hd0) is /dev/sda, but in your case it is /dev/hdc.  Then reinstall grub with sudo grub-install.

I've tried every other solution possible, and this seems like something I have yet to try. Could you (or anyone else) elaborate on this? It sounds really promising, but I'm still really new at this, so I need more elaborate instructions.

Thanks to everyone who's come up with ideas so far. I tried the super grub disk, and it hasn't really gotten me anywhere, but thanks for the idea!

---

### Post by meierfra on 2007-12-29
Try this.

Open and backup  "menu.lst" via


```
mkdir boot
sudo mount -t ext2   /dev/hdc1 boot
cd boot/grub
cp menu.lst menu.lst.backup
gksudo gedit  menu.lst
```


Look for the lines

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd?,?)

change it to

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)


Save and close the file


In the terminal:

```
sudo grub
```


and at the "grub>" prompt

```
find /grub/stage1
```
the output should be (hdx,0) where x is some number, probably it is (hd2,0)

```
root (hdx,0)
setup (hdx)
quit
```
(here x needs to  replaced by the actually number  found above) 


Reboot, but make sure that the Ubuntu drive is first in the boot order in the bios.

---

### Post by pietjanjaap on 2007-12-29
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

This means that the bios does not find a bootloader/operating system
This means 1. wrong bootdisk choosen
                    2. grub not installed

So if your choosen bootdisk is ok then download supergrub, and install this, then you can boot again, supergrub wil see windows/linux and make a list.
The only thing is that you have to change the (hd0,0) or (hd0,1) etc.


This is how ubuntu/pc starts,
first choose the wright disk
then grub starts
then menu.lst
then ubuntu

so if there is something not ok then search in the list.

---

### Post by psusi on 2007-12-30
> **nicklikesfire said:**
> I've tried every other solution possible, and this seems like something I have yet to try. Could you (or anyone else) elaborate on this? It sounds really promising, but I'm still really new at this, so I need more elaborate instructions.

Thanks to everyone who's come up with ideas so far. I tried the super grub disk, and it hasn't really gotten me anywhere, but thanks for the idea!

Open the file and edit the entries so they line up properly with your bios disk order.  For instance, if you have the bios set to boot from /dev/sdb, then make sure that (hd0) points there.

---

