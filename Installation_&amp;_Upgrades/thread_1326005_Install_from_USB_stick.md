---
title: "Install from USB stick"
date: 2009-11-14
forum: Installation &amp; Upgrades
---

### Post by p2ranger on 2009-11-14
I've been seeing other people having issues making a USB stick to use for installing Ubuntu 9.10. The usb-creator.exe file is no longer in the ISO. So the page [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
is no longer valid.

I have a new computer with no CD rom drive on it that I'm trying to install Ubuntu 9.10 server on. The best I've gotten it to do so far is to get past the language selection, keyboard layout, and then it says it can't find the CD-ROM drive. I've tried making images on the USB drive from just copying the files straight over on to it from after burning the CDROM, I've tried using the USB Startup Disk Creator in Ubuntu, and I just can't seem to get this installation to work. Has anyone else had any luck installing from a USB stick with 9.10? If so, how did you do it?

The specific error I get after selecting the keyboard is:
```

Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Try again to mount the CD-ROM?

<Yes>   <No>
```

I haven't tried UNetbootin because I only have a 1 GB USB stick and it says you need a 2 GB.

Thanks

Jason

---

### Post by efflandt on 2009-11-14
I have installed both 32 and 64-bit 9.10 install iso on USB stick made with System, Administration, **USB Startup Disk Creator**, which should still be there if you can boot the install CD live on another computer (unless something changed since 9.10 was released).  But that was on 4 G so I usually left 1 to 2 G of original file space remaining in case I wanted to use it for Windows files.

Booting install from USB usually mounts the partition it boots from as /cdrom, so not having a cdrom should not be an issue unless something else went wrong.

Just for the fun of it I tried using USB Startup Disk Creator on 2G microSD (which showed up as /dev/mmcblk0 and partition mmcblk0p1 in laptop SD slot), but I tried to allot total remaining space for persistent data, and that failed with an error that it could not complete and when I tried to mount that partition, it errored that something was missing.  When I put the microSD in a card reader (/dev/sdb), reformatted sdb1, and likewise tried to allot entire remaining space to persistent data, it said it was 100% complete, but hung there with the only choice of Cancel.  When I tried to boot, it got past language selection, and live boot selection, but hung with black screen after Ubuntu logo.

I suspected that USB Creator files were using slightly more space than estimated (files not ending on sector boundaries).  So I selected a persistent file one click down from remaining space and then everything worked.  It completed and I was able to boot from it.  So when using **USB Startup Disk Creator**, make sure that you do **not** use all of remaining space for persistent data (slider at least one click down from end).

Note that casper-rw is the ext3 loop mounted filesystem for persistent data, so yours would be smaller on 1 G.

```
**ls -l /media/CC67-4B4B**
total 1134336
-rwxr-xr-x 1 efflandt efflandt        143 2009-11-14 10:39 autorun.inf
drwx------ 2 efflandt efflandt      32768 2009-11-14 10:42 casper
-rwxr-xr-x 1 efflandt efflandt 1159725056 2009-11-14 10:45 casper-rw
drwx------ 3 efflandt efflandt      32768 2009-11-14 10:42 dists
drwx------ 2 efflandt efflandt      32768 2009-11-14 10:42 install
-r-xr-xr-x 1 efflandt efflandt      14607 2009-11-14 10:39 ldlinux.sys
-rwxr-xr-x 1 efflandt efflandt       4199 2009-11-14 10:39 md5sum.txt
drwx------ 2 efflandt efflandt      32768 2009-11-14 10:42 pics
drwx------ 4 efflandt efflandt      32768 2009-11-14 10:42 pool
drwx------ 2 efflandt efflandt      32768 2009-11-14 10:42 preseed
-rwxr-xr-x 1 efflandt efflandt        225 2009-11-14 10:39 README.diskdefines
drwx------ 2 efflandt efflandt      32768 2009-11-14 10:42 syslinux
-rwxr-xr-x 1 efflandt efflandt    1468640 2009-11-14 10:39 wubi.exe

**grep usb /media/CC67-4B4B/casper/filesystem.manifest**
libusb-0.1-4 2:0.1.12-13
usb-creator-common 0.2.12
usb-creator-gtk 0.2.12
usbutils 0.82-0ubuntu1
xserver-xorg-video-sisusb 1:0.9.1-1
```USB memory is cheap up to a point.  The last 2 G I bought was $9.95 and Best Buy currently has 8 G Sandisk Cruzer for $24.95US.

---

### Post by darkod on 2009-11-14
I have installed UNR 9.10 and desktop 32bit 9.10 from USB stick on my netbook without any problems. Both installs went perfect. Didn't like the menu layout of UNR so installed desktop version over it two days later.

---

### Post by p2ranger on 2009-11-14
Got it to work. I used unetbootin
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Used the 9.10 server .iso and created the bootable USB stick using the windows flavor of unetbootin

Thanks for the help :D
 
Jason

---

### Post by duanedesign on 2010-01-02
Guide to creating a Llive USB:
[http://ubuntuforums.org/showthread.php?t=1193680](http://ubuntuforums.org/showthread.php?t=1193680)

**Known Issues**
The 9.10 CDs and DVDs are [COLOR="Red"]missing the usb-creator.exe program[/COLOR]. To install to a flash drive from a disk image on Windows, use the process described at:
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/) 
-
-
-

---

