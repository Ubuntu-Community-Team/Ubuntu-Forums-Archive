---
title: "[SOLVED] Bootable USB Pen Drive"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by tech9 on 2007-11-13
I installed ubuntu 7.04 on my USB thumb drive, but am not able to save any files directly to the removable drive. I made sure that I formatted the drive as vfat. I also booted up in persistent mode - to be able to make/save changes, but that did not work either.

Does anybody have any ideas why this is happening? 

I tried this site....
[http://www.pendrivelinux.com](http://www.pendrivelinux.com)

What would you recommend as a good linux OS to boot from a USB Stick?

---

### Post by tech9 on 2007-11-15
forget it, I don't know why I even bother asking for help!

---

### Post by staticvoid on 2007-11-15
you only waited 2 days and gave up?

you should try puppy linux. its made great for a pendrive, plus the have documentation on howto do it. :D

sv

---

### Post by tech9 on 2007-11-15
> **staticvoid said:**
> you only waited 2 days and gave up?

you should try puppy linux. its made great for a pendrive, plus the have documentation on howto do it. :D

sv

Thanks! I will look into it :)

Does this OS allow you to write files to the USB Drive?

---

### Post by Herman on 2007-11-15
Probably you are asking questions about subject that not so many others have tried out for themselves.
You just need to wait longer for a reply for some subjects, bumping does help if you have waited like, 2 days or something. :)

Okay, there are different ways to install Ubuntu to a USB disk.

If it's a small USB disk like a USB flash disk, say 1.) GB in size or a little more, you can install Ubuntu to it and it will run as a Live CD. As we all know, we can't save files or changes to a Live CD operating system over a reboot. They just don't work that way.
A Ubuntu Live CD in a USB flash memory stick is great if you have a computer that can boot one of those. It beats the heck out of a real Live CD for speed! :)
And you can use it to install Ubuntu without CD-ROM drive read errors too, or even if you don;t have a working CD-ROM drive.


A Ubuntu operating system installed in a large external USB hard drive is a lot different. You have a choice of installing as a Live CD type of install as mentioned above or you can install Ubuntu in the external USB drive in the regular way, the same as your do when you are installing to any other hard disk. 
With that kind of USB operatng system you can save files and settings and all that over a reboot, just the same as an proper internal hard drive installed Ubuntu operating system.

Problems with installing Ubuntu to an external USB drive like that are
1. Booting, you need to know a bit about GRUB to know how to get it to boot. Not all computer support booting the USB either.
2. Hardware. It isn't like a LiveCD anymore, it won't automatically set itself up for the hardware in any computer you plug it into, so you will probably need to run sudo dpkg-reconfigure xserver.xorg every time you try to boot it in a different machine.
3. Human error. A USB drive is a hard drive in a box. Normally, a desktop computer box remains on a desk and we don't handle it handled much, especially while it's running. Small USB disks tend to be lifted and shifted when you, (or a freind) is looking for something that's lost, and if they are running when they slip out of  a human hand and fall  on the floor, you lose  everything when the heads contact the spinning disk surface and physically damage the hard disk drive. 
4. You lose, (or at least limit) the use of your USB drive as a convenient and important media for backing up data on. External USB drives are really great for making speedy data backups! That's what they are really meant for.  And then leave them powered off for most of the day so even if they do get handled, they're more likely not to be spinning at the time. Much smarter way to use a large external USB hard disk drive.
It can be removed from the external enclosure and plugged into an IDE cable inside the computer if it's to have an operating system in it.

The excellent how-to that you followed seems to be for installing the LiveCD to a flash memory stick, so I guess it runs as a Live CD, and it does say that you should be able to save changes over a re-boot. That's extremely smart. I imagine that would have something to do with the boot options in syslinux, for casper, so you would look for a mistake in the boot options. That how to seems quite advanced and you would need to be either an advanced user or someone who is careful and patient, to make sure you do everything perfect.

I made a how-to about [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406&highlight=Ubuntu+supergrub+usb") if that will help you. I used a USB flash memory stick that was bigger than I needed just for the Ubuntu LiveCD, so I showed how to make a separate partition in the USB flash memory disk to copy a few files to.
The worst thing about my how-to is although it's a lot simpler, I don't know all the boot options to boot the LiveCD in special ways with GRUB.
I would like to learn how to chainload syslinux from GRUB and I would like to learn more about syslinux too.
So the excellent how-to you already followed is probably better than my effort on the subject.
Mine will allow you to save files, but probably not in the way you really wanted, and you'll have Super Grub Disk in it.

The easiest thing is to install Ubuntu in an internal hard disk like it's designed for.

I have a web page about Knoppix that explains how to use a USB of either kind, (a USB flash memory stick or an USB external hard disk drive), with a Knoppix DVD (or CD), which is really good. [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html").
Knoppix is designed for that kind of use, and your information will be encrypted too, in case you lose your memory stick and there might be sensitive data on it.

I also agree with staticvoid and tech9, I'm a Puppy Linux fan too! :)
If you install Puppy Linux to a USB drive, you will be using a distribution that is meant to be easily installed and used from a pendrive. You'll have a lot less headaches using Linux distros for whatever they were designed for.

Regards, Herman :)

---

### Post by tech9 on 2007-11-15
> **Herman said:**
> Probably you are asking questions about subject that not so many others have tried out for themselves.
You just need to wait longer for a reply for some subjects, bumping does help if you have waited like, 2 days or something. :)

Okay, there are different ways to install Ubuntu to a USB disk.

If it's a small USB disk like a USB flash disk, say 1.) GB in size or a little more, you can install Ubuntu to it and it will run as a Live CD. As we all know, we can't save files or changes to a Live CD operating system over a reboot. They just don't work that way.
A Ubuntu Live CD in a USB flash memory stick is great if you have a computer that can boot one of those. It beats the heck out of a real Live CD for speed! :)
And you can use it to install Ubuntu without CD-ROM drive read errors too, or even if you don;t have a working CD-ROM drive.


A Ubuntu operating system installed in a large external USB hard drive is a lot different. You have a choice of installing as a Live CD type of install as mentioned above or you can install Ubuntu in the external USB drive in the regular way, the same as your do when you are installing to any other hard disk. 
With that kind of USB operatng system you can save files and settings and all that over a reboot, just the same as an proper internal hard drive installed Ubuntu operating system.

Problems with installing Ubuntu to an external USB drive like that are
1. Booting, you need to know a bit about GRUB to know how to get it to boot. Not all computer support booting the USB either.
2. Hardware. It isn't like a LiveCD anymore, it won't automatically set itself up for the hardware in any computer you plug it into, so you will probably need to run sudo dpkg-reconfigure xserver.xorg every time you try to boot it in a different machine.
3. Human error. A USB drive is a hard drive in a box. Normally, a desktop computer box remains on a desk and we don't handle it handled much, especially while it's running. Small USB disks tend to be lifted and shifted when you, (or a freind) is looking for something that's lost, and if they are running when they slip out of  a human hand and fall  on the floor, you lose  everything when the heads contact the spinning disk surface and physically damage the hard disk drive. 
4. You lose, (or at least limit) the use of your USB drive as a convenient and important media for backing up data on. External USB drives are really great for making speedy data backups! That's what they are really meant for.  And then leave them powered off for most of the day so even if they do get handled, they're more likely not to be spinning at the time. Much smarter way to use a large external USB hard disk drive.
It can be removed from the external enclosure and plugged into an IDE cable inside the computer if it's to have an operating system in it.

I made a how-to about [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406&highlight=Ubuntu+supergrub+usb") if that will help you. I used a USB flash memory stick that was bigger than I needed just for the Ubuntu LiveCD, so I shwed how to make a separate partition in the USB flash memory disk to copy a few files to.
The worst thing about my how-to is I don't know all the boot options to boot the LiveCD in special ways with GRUB.
I would like to learn how to chainload syslinux from GRUB and I would like to learn more about syslinux too.
So the how-to you already followed is probably better than mine.
Mine will allow you to save files, but probably not in the way you really wanted.

The best thing is to install Ubuntu in an internal hard disk like it's designed for.

I have a web page about Knoppix that explains how to use a USB of either kind, (a USB flash memory stick or an USB external hard disk drive), with a Knoppix DVD (or CD), which is really good. [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html").
Knoppix is designed for that kind of use, and your information will be encrypted too, in case you lose your memory stick and there might be sensitive data on it.

I also agree with staticvoid and tech9, I'm a Puppy Linux fan too! :)
If you install Puppy Linux to a USB drive, you will be using a distribution that is meant to be easily installed and used from a pendrive. You'll have a lot less headaches using Linux distros for whatever they were designed for.

Regards, Herman :)

Thanks for your input Herman... I was able to create a bootable USB stick with feisty... the only problem I am having is that I cannot save data/files to the the USB Drive. Also, when I cannot save changes to the system, even when in persistent mode... it's very strange#-o

---

### Post by Herman on 2007-11-15
I edited my post just before you replied, my bet would be it has something to do with your boot options in syslinux.
 Look for some mistake in there somewhere, probably, I'm only guessing so I might be wrong.

Regards, Herman :)

---

### Post by tech9 on 2007-11-15
> **Herman said:**
> I edited my post just before you replied, my bet would be it has something to do with your boot options in syslinux.
 Look for some mistake in there somewhere, probably, I'm only guessing so I might be wrong.

Regards, Herman :)

I am pretty good with linux, but I am no expert. I am not quite sure what I am looking for... 

Here is the output of my syslinux file...

  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- 
LABEL live 
  menu label ^Start or install Ubuntu 
  kernel vmlinuz 
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- 
LABEL xforcevesa 
  menu label Start Ubuntu in safe ^graphics mode 
  kernel vmlinuz 
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- 
LABEL check 
  menu label ^Check CD for defects 
  kernel vmlinuz 
  append  boot=casper integrity-check initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- 
LABEL memtest 
  menu label ^Memory test 
  kernel mt86plus 
  append - 
LABEL hd 
  menu label ^Boot from first hard disk 
  localboot 0x80 
  append - 
DISPLAY isolinux.txt 
TIMEOUT 300 
PROMPT 1 
F1 f1.txt 
F2 f2.txt 
F3 f3.txt 
F4 f4.txt 
F5 f5.txt 
F6 f6.txt 
F7 f7.txt 
F8 f8.txt 
F9 f9.txt 
F0 f10.txt

Thanks for your help Herman! :)

---

### Post by Herman on 2007-11-16
Hello tech9,
My guess is you are missing some lines from the top of your syslinux.cfg file.
I haven't read all the way through there how-tos and studied them in sufficient detail or tried them out yet, so take my guess here with a grain of salt. 
Just compare your syslinux.cfg with the one from this how-to, [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

```
[COLOR=Sienna][B]DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL persistent
  menu label Start Ubuntu 7.10 in ^persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz quiet splash --[/B][/COLOR]
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```Maybe try pasting in the lines I have hilighted in green and see if that works.

Here are a few more links as well, 
[Installation/FromUSBStick - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/FromUSBStick")

[Preparing Files for USB Memory Stick Booting]("https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html")

[How-to: Installing Ubuntu Linux on a usb pendrive | Debian/Ubuntu Tips & Tricks]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar")

I will get around to trying those out for myself and studying and practicing with syslinux sometime soon, but some other work I had to get done took longer than expected and I didn't want to keep you waiting.

Let me know if it works or not and if you still have trouble I'll see what I can do to about getting around to testing these myself a little quicker so I can help you better.

Regards, Herman :)

---

### Post by Rhubarb on 2007-11-16
I haven't tried getting fiesty to work in persistence mode on a usb stick, but I have successfully gotten gutsy working fine with persistency.  I can save files, make changes, and it all remembers it.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by tech9 on 2007-11-16
> **Herman said:**
> Hello tech9,
My guess is you are missing some lines from the top of your syslinux.cfg file.
I haven't read all the way through there how-tos and studied them in sufficient detail or tried them out yet, so take my guess here with a grain of salt. 
Just compare your syslinux.cfg with the one from this how-to, [LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

```
[COLOR=Sienna][B]DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL persistent
  menu label Start Ubuntu 7.10 in ^persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=initrd.gz quiet splash --[/B][/COLOR]
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```Maybe try pasting in the lines I have hilighted in green and see if that works.

Here are a few more links as well, 
[Installation/FromUSBStick - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/FromUSBStick")

[Preparing Files for USB Memory Stick Booting]("https://help.ubuntu.com/7.04/installation-guide/i386/boot-usb-files.html")

[How-to: Installing Ubuntu Linux on a usb pendrive | Debian/Ubuntu Tips & Tricks]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar")

I will get around to trying those out for myself and studying and practicing with syslinux sometime soon, but some other work I had to get done took longer than expected and I didn't want to keep you waiting.

Let me know if it works or not and if you still have trouble I'll see what I can do to about getting around to testing these myself a little quicker so I can help you better.

Regards, Herman :)

Hi Herman,

I tried copying and pasting the lines that you highlighted in the syslinux file and still not successful with saving changes to the OS.  I think I may try installing gutsy on the stick, and see if I have any success with that. I really appreciate all of your help! :)

Thanks!

T9

---

### Post by tech9 on 2007-11-16
> **Rhubarb said:**
> I haven't tried getting fiesty to work in persistence mode on a usb stick, but I have successfully gotten gutsy working fine with persistency.  I can save files, make changes, and it all remembers it.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Oh oh, I think I destroyed my USB Pen Drive...

See details...

admin1@admin1-desktop:~$ sudo umount /dev/sdb2
[sudo] password for admin1:
umount: /dev/sdb2: not found
admin1@admin1-desktop:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not found
admin1@admin1-desktop:~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
admin1@admin1-desktop:~$ fdisk /dev/sdb

Unable to open /dev/sdb
admin1@admin1-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbaebbaeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4620    37110118+  83  Linux
/dev/sda2            4621        4865     1967962+  82  Linux swap / Solaris
admin1@admin1-desktop:~$ 

/dev/sdb1 & /dev/sdb2 are gone... my stick is plugged into the PC too:-k

my usb stick will not pick up in windoz either... PNP does not detect.

---

### Post by Rhubarb on 2007-11-18
Go into System --> Administration --> System Log
Pluy your USB flash drive in, and see what messages come up.

I don't think it's possible to screw up your USB flash drive even if you tried to.
Try running gparted (you may have to install it if you haven't already done so), and check to see if it can find any partitions there.

---

### Post by fisting_mayfield on 2007-11-18
Hi,
This post seems handy...
I've been trying to get 7.10 installed onto a usb stick for use at uni (i cant handle having to use windows!!)
I've previously followed the how-to from pendrivelinux.com, however i get grub errors when i try and boot to the usb stick...
I'll try some of the suggestions listed on this thread, and post up my results.

(sorry to tread-jack you T9!)

---

### Post by tech9 on 2007-11-19
> **Rhubarb said:**
> Go into System --> Administration --> System Log
Pluy your USB flash drive in, and see what messages come up.

I don't think it's possible to screw up your USB flash drive even if you tried to.
Try running gparted (you may have to install it if you haven't already done so), and check to see if it can find any partitions there.

Thanks for the advice, I actually saw no log activity, no error messages, nothing - I already tossed it because it was a cheap no-brand pen.

I believe I messed it up by pulling the drive before fully shutting down the system. 

my fault completely.... ](*,)

I ordered a corsair 1GB stick, I am going to try this all over again....
I will keep you all posted with my progress

---

### Post by tech9 on 2007-11-19
> **fisting_mayfield said:**
> Hi,
This post seems handy...
I've been trying to get 7.10 installed onto a usb stick for use at uni (i cant handle having to use windows!!)
I've previously followed the how-to from pendrivelinux.com, however i get grub errors when i try and boot to the usb stick...
I'll try some of the suggestions listed on this thread, and post up my results.

(sorry to tread-jack you T9!)

That's ok, I hope that you get your problems resolved too 8-)

---

### Post by bignickel on 2007-11-20
I'm trying to boot xubuntu from a USB stick.  I recently got a hold of an HP T5520 thin client, which normally runs Windows CE, but the first thing I did was get rid of that.  It supports USB booting, and I thought I'd try xubuntu since it only has 128 MB RAM.  I made the stick bootable, and put the Gutsy CD on it using the instructions at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent").  

It starts up and starts loading, but when it launches X the screen goes blank.  I tried the Feisty Xubuntu release and the same thing happened.  I also tried Damn Small Linux, and although I could get it to boot I can't make it stay persistent.  I realize it's a bit of a long shot, but any suggestions anyone?

---

### Post by tech9 on 2007-11-21
> **bignickel said:**
> I'm trying to boot xubuntu from a USB stick.  I recently got a hold of an HP T5520 thin client, which normally runs Windows CE, but the first thing I did was get rid of that.  It supports USB booting, and I thought I'd try xubuntu since it only has 128 MB RAM.  I made the stick bootable, and put the Gutsy CD on it using the instructions at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent).  

It starts up and starts loading, but when it launches X the screen goes blank.  I tried the Feisty Xubuntu release and the same thing happened.  I also tried Damn Small Linux, and although I could get it to boot I can't make it stay persistent.  I realize it's a bit of a long shot, but any suggestions anyone?

Well, it looks like we are in the same boat as far as being able to make changes to the OS, but not sure about your stick booting to a blank screen. I was able to boot up into Gutsy... I am trying all over from scratch once my new stick arrives.

I will keep you all posted on my progress.

---

### Post by Herman on 2007-11-25
Originally posted by Rhubarb,
> I haven't tried getting fiesty to work in persistence mode on a usb stick, but I have successfully gotten gutsy working fine with persistency. I can save files, make changes, and it all remembers it.
[http://www.pendrivelinux.com/2007/09...ibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/"):) I have spent the whole weekend learning about Isolinux and Syslinux and all the wrong ways to try to get a Ubuntu LiveCD in a USBdisk to boot in persistent mode.

I have learned all kinds of things along the way that might come in handy for something else some day, but the only way I finally got it to work was by using the link that Rhubarb provided. 
Thanks Rhubarb! :guitar:

The key part of that was to download U710fix.zip from pendrivelinux.com/downloads and install it.

I used the Ubuntu Wiki's tutorial to get me started (well, after I tried lots of things and realized I wasn't getting anywhere actually), [LiveCDPersistence]("https://help.ubuntu.com/community/LiveCDPersistence"), that was a big help to me because I could break the problem down that way. At least if I could get a Live CD to be persistent to start with then I could understand better what to do with the USBdisk.

The main how-to I used was this one, [LiveUSBPendrivePersistence]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), but I used [GParted -- LiveCD]("http://gparted.sourceforge.net/") to do the partitioning and filesystem work.

I already knew the command for labelling the FAT32 file system, here is my own link about that, [fat32 usbdisk volume label]("http://users.bigpond.net.au/hermanzone/p10.htm#fat32_usbdisk_volume_label")
(to create the FAT32 file system for the CD files and label it ubuntu or if you like ubuntu710. WARNING: that command will format the partition with a new FAT32 file system, so don't use it for a partition with data in it!

I also have a link for helping people label an ext3 file system, that can be done from a terminal in GParted LiveCD too, or any terminal, [Make a label your ext3 usbdisk]("http://users.bigpond.net.au/hermanzone/p10.htm#ext3_usbdisk_labelling"). The command for labelling an ext2 or ext3 file system is safe to use anytime.
That's to label your 'casper-rw' file system where the changes will be saved to.

In the end, it was Rhubarb's link that finally got me across the finish line. I'm exhausted! :lolflag: But happy!

bignickel, you said:
>  It starts up and starts loading, but when it launches X the screen goes blank. I get that too but I'm not sure if it's the same as what you are talking about or not. Mine goes black, but when I press my 'Enter' key it shows the desktop. 

Good luck everyone, I'll be around if you still need help. My weekdays are a little hectic sometimes. I'll be here twice a day though.

Regards, Herman :)

---

### Post by tech9 on 2007-11-27
> **Herman said:**
> Originally posted by Rhubarb,
:) I have spent the whole weekend learning about Isolinux and Syslinux and all the wrong ways to try to get a Ubuntu LiveCD in a USBdisk to boot in persistent mode.

I have learned all kinds of things along the way that might come in handy for something else some day, but the only way I finally got it to work was by using the link that Rhubarb provided. 
Thanks Rhubarb! :guitar:

The key part of that was to download U710fix.zip from pendrivelinux.com/downloads and install it.

I used the Ubuntu Wiki's tutorial to get me started (well, after I tried lots of things and realized I wasn't getting anywhere actually), [LiveCDPersistence]("https://help.ubuntu.com/community/LiveCDPersistence"), that was a big help to me because I could break the problem down that way. At least if I could get a Live CD to be persistent to start with then I could understand better what to do with the USBdisk.

The main how-to I used was this one, [LiveUSBPendrivePersistence]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent"), but I used [GParted -- LiveCD]("http://gparted.sourceforge.net/") to do the partitioning and filesystem work.

I already knew the command for labelling the FAT32 file system, here is my own link about that, [fat32 usbdisk volume label]("http://users.bigpond.net.au/hermanzone/p10.htm#fat32_usbdisk_volume_label")
(to create the FAT32 file system for the CD files and label it ubuntu or if you like ubuntu710. WARNING: that command will format the partition with a new FAT32 file system, so don't use it for a partition with data in it!

I also have a link for helping people label an ext3 file system, that can be done from a terminal in GParted LiveCD too, or any terminal, [Make a label your ext3 usbdisk]("http://users.bigpond.net.au/hermanzone/p10.htm#ext3_usbdisk_labelling"). The command for labelling an ext2 or ext3 file system is safe to use anytime.
That's to label your 'casper-rw' file system where the changes will be saved to.

In the end, it was Rhubarb's link that finally got me across the finish line. I'm exhausted! :lolflag: But happy!

bignickel, you said:
 I get that too but I'm not sure if it's the same as what you are talking about or not. Mine goes black, but when I press my 'Enter' key it shows the desktop. 

Good luck everyone, I'll be around if you still need help. My weekdays are a little hectic sometimes. I'll be here twice a day though.

Regards, Herman :)

Wow Herman! :) Thank you for spending all this time to help me out. I just got my brand new 1 GB corsair stick. I will try all of your suggestions and let you know it worked for me.

---

### Post by tech9 on 2007-11-27
Here is the latest...

when I follow all of the direction from this link... 
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and I get to step 10, I get the following error....

admin@admin-desktop:~$ sudo umount /dev/sdb2
umount: /dev/sdb2: not found

____________________________________________________

the partition is created see below...

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         705      733184    6  FAT16
/dev/sdb2             706         945      249600   83  Linux

____________________________________________________

then when I try step 11

I get this...

admin@admin-desktop:~$ mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
mke2fs 1.40.2 (12-Jul-2007)

Could not stat /dev/sdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

____________________________________________________________

This is where I am stuck!
 Any ideas or suggestions are welcome :)

---

### Post by tech9 on 2007-11-27
> **tech9 said:**
> Here is the latest...

when I follow all of the direction from this link... 
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and I get to step 10, I get the following error....

admin@admin-desktop:~$ sudo umount /dev/sdb2
umount: /dev/sdb2: not found

____________________________________________________

the partition is created see below...

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         705      733184    6  FAT16
/dev/sdb2             706         945      249600   83  Linux

____________________________________________________

then when I try step 11

I get this...

admin@admin-desktop:~$ mkfs.ext2 -b 4096 -L casper-rw /dev/sdb2
mke2fs 1.40.2 (12-Jul-2007)

Could not stat /dev/sdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?

____________________________________________________________

This is where I am stuck!
 Any ideas or suggestions are welcome :)

I used gparted to fix finding the second partition... I am still working on configuring the stick

---

### Post by Herman on 2007-11-28
> I used gparted to fix finding the second partition... I am still working on configuring the stick 	 Okay, sorry I wasn't here in time to help. I probably would have suggested using GParted. 
Keep up the good work,
Regards, Herman :)

---

### Post by tech9 on 2007-11-28
> **Herman said:**
> Okay, sorry I wasn't here in time to help. I probably would have suggested using GParted. 
Keep up the good work,
Regards, Herman :)

Hi Herman,

  Here's where I am at...

 when I try to run this command, [B]
wget pendrivelinux.com/downloads/U710fix.zip 

to get the U710fix.zip
[/B]
I get this...

Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Retrying.

--13:32:10--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try: 2) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Retrying.

--13:37:21--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try: 3) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Retrying.

--13:42:33--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try: 4) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... 

.
.
.
.
.--15:44:35--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try:18) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Retrying.

--15:49:54--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try:19) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Retrying.

--15:55:13--  [http://pendrivelinux.com/downloads/U710fix.zip](http://pendrivelinux.com/downloads/U710fix.zip)
  (try:20) => `U710fix.zip'
Connecting to pendrivelinux.com|69.89.27.206|:80... failed: Connection timed out.
Giving up.


Is there a place where I can manually download and install the U710fix.zip file?

---

### Post by Herman on 2007-11-28
Here's what you should see,
```
herman@amd46b:~$ wget pendrivelinux.com/downloads/U710fix.zip 
--13:00:59--  http://pendrivelinux.com/downloads/U710fix.zip
           => `U710fix.zip.1'
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 939 [application/zip]

100%[====================================>] 939           --.--K/s             

13:01:00 (74.54 MB/s) - `U710fix.zip.1' saved [939/939]
 
```You might want to try it again one more time. If it still doesn't work I'll send you my copy of it, please find the attachment to this post.

Generally, it is considered an unsafe practice to download and install software from any but the official Ubuntu repositories. Download the file at your own risk.
However, I have tested it and it works well for me without any problems that I know of, and I have not modified the file in any way. I value my reputation here and I wouldn't want to do any harm to anyone's computer or compromise their security in any way. So long as you are aware that you are trusting me it's okay to download it and use it, but just be aware so you won't fall into a habit of doing this kind of thing without thinking it over first.

Regards, Herman :)

---

### Post by brokenbones on 2007-11-29
Hello,

I am in the same boat as you, and I described it in another thread, but I could as well go on here since I got no useful answer.

The problem seems to be the second partition (sdb2 for me too), that doesn't get mounted when booting from the USB stick. If I boot from the CD to a Live session and plug in my stick, both partitions are there and work fine. When booting from the stick, only the first partition work in a non persistent way, and gparted reports that partition 2 cound not be mounted since no mountpoint could be found.

Using a 4GB Kingston DataTraveller and the Gutsy LiveCD.

I wonder if using another boot manager (GRUB, LILO) could fix this ?

Lorenzo

---

### Post by tech9 on 2007-11-29
> **Herman said:**
> Here's what you should see,
```
herman@amd46b:~$ wget pendrivelinux.com/downloads/U710fix.zip 
--13:00:59--  http://pendrivelinux.com/downloads/U710fix.zip
           => `U710fix.zip.1'
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 939 [application/zip]

100%[====================================>] 939           --.--K/s             

13:01:00 (74.54 MB/s) - `U710fix.zip.1' saved [939/939]
 
```You might want to try it again one more time. If it still doesn't work I'll send you my copy of it, please find the attachment to this post.

Generally, it is considered an unsafe practice to download and install software from any but the official Ubuntu repositories. Download the file at your own risk.
However, I have tested it and it works well for me without any problems that I know of, and I have not modified the file in any way. I value my reputation here and I wouldn't want to do any harm to anyone's computer or compromise their security in any way. So long as you are aware that you are trusting me it's okay to download it and use it, but just be aware so you won't fall into a habit of doing this kind of thing without thinking it over first.

Regards, Herman :)

Hi Herman,

Thanks for attaching the files I need. I do realize that it is best to get everything from the repositories, but I am behind a proxy... I think that may have something to do with it. Also, I trust you. I wouldn't normally download files manually like this. I have already installed ntlmaps so that I can still run sudo atp-get
I tried it one more time and it did not resolve again... probably the proxy thing.

well, my question now is I see the the linux boot file is named completely different in 710 than in 704 . The name of 710 boot file is ldlinux.sys and 704 is syslinux.cfg.

I extracted the two files  syslinux.cfg & isolinux.txt in the root of my USB drive.

Is there something that I am missing?

when I try to boot the stick, I receive an error message saying "Error loading operating system.

Thanks Herman :)

T9

---

### Post by tech9 on 2007-11-29
> **brokenbones said:**
> Hello,

I am in the same boat as you, and I described it in another thread, but I could as well go on here since I got no useful answer.

The problem seems to be the second partition (sdb2 for me too), that doesn't get mounted when booting from the USB stick. If I boot from the CD to a Live session and plug in my stick, both partitions are there and work fine. When booting from the stick, only the first partition work in a non persistent way, and gparted reports that partition 2 cound not be mounted since no mountpoint could be found.

Using a 4GB Kingston DataTraveller and the Gutsy LiveCD.

I wonder if using another boot manager (GRUB, LILO) could fix this ?

Lorenzo

do the following to solve your issue...

sudo apt-get gparted

after it finishes installing 

goto System>Administration>Partition Editor

Select partition /dev/sdb2

right click choose ext2

click apply...

this should fix your problem 8-)

---

### Post by Herman on 2007-11-29
:) Hello tech9,
> Thanks for attaching the files I need. I do realize that it is best to get everything from the repositories, but I am behind a proxy... I think that may have something to do with it. I have already installed ntlmaps so that I can still run sudo atp-get Okay, sorry about that, I wanted to put that message there though,* mainly for other people who may also be reading this thread*. I don't want to be setting a bad example that others might follow, hence the warning. :)
>  well, my qustion now is I see the the linux boot file is named completely different in 710 than in 704 . The name of 710 boot file is ldlinux.sys and 704 is syslinux.cfg.
I extracted the two files  syslinux.cfg & isolinux.txt in the root of my USB drive.
Is there something that I am missing?
when I try to boot the stick, I receive an error message saying "Error loading operating system. Did you install syslinux to the MBR of the flash drive or to the first sector or the ubuntu710 partition?

Quote from the how-to, 
> 12 Remove and Re-insert your flash drive
13 Back at the terminal, type **apt-get update**
14 Type **apt-get install syslinux mtools**
15 Type **syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1**That would install syslinux to the first sector of the **ubuntu710 **partition, to install syslinux to the MBR of the USB disk, you would need to do,
15 (b) Type [B]syslinux -sf /dev/sd[COLOR=#ff0000]x
[/COLOR][/B]```
syslinux -sf /dev/sdx
```Actually, with my own particular USB setup, I didn't run into that problem because I made mine a little different. Mine has [Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb") in the first partition and installed to the flash drive's MBR and the ubuntu and casper-rw partitions are after that. I edited Super Grub Disk for USB's menu.lst to chainload syslinux in the first sector of the flash drive's ubuntu partition.
I also added lines in my regular (internal hard drive's) Ubuntu's GRUB menu to chainload either the MBR of the USB, (Super Grub DIsk for USB), or the second partition in the USB, syslinux, which boots ubuntu in the USB.

Anyway, tech9, just try installing syslinux to MBR as well as to the partition of your USB flash drive and see if it works then.

Or try chainloading the USB's first partition from your installed GRUB and that should work too.

EDIT: I just re-tried this myself and the advice about installing Syslinux to MBR is incorrect, you will get this, "syslinux: this doesn't look like a valid FAT filesystem".
As the how-to suggests, you can install LiLo to MBR in the USBdisk instead, (or GRUB, or Super Grub Disk like I did.)

Will that help you or did I guess wrong about what your problem might be? 

Regards, Herman :)

---

### Post by Herman on 2007-11-29
:) Hello brokenbones,
>  Using a 4GB Kingston DataTraveller and the Gutsy LiveCD.Me too! :)
> The problem seems to be the second partition (sdb2 for me too), that doesn't get mounted when booting from the USB stick. If I boot from the CD to a Live session and plug in my stick, both partitions are there and work fine. When booting from the stick, only the first partition work in a non persistent way, and gparted reports that partition 2 cound not be mounted since no mountpoint could be found.
Another thing it could be if you tried tech9's good advice already and it still doesn't work,  did you label your second partition 'casper-rw' with the e2label command?
Note that the correct label is 'casper-rw' (without the inverted commas), and there is no whitespace (gap) between the word 'casper' and the '-rw' part of the label, or it will cause problems for you.
Unlike with the FAT32 file system, the e2label command can make a new label for the ext2 or ext3 file system without reformatting the file system and losing all the data, so you can check this and if necessary change your file system label any time.

Regards, Herman.

---

### Post by tech9 on 2007-11-29
Hi Herman,

I tried following already
Quote from the how-to, 
     Quote:
                                                 12 Remove and Re-insert your flash drive
13 Back at the terminal, type **apt-get update**
14 Type **apt-get install syslinux mtools**
15 Type **syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1**                                 
That would install syslinux to the first sector of the **ubuntu710 **partition, to install syslinux to the MBR of the USB disk, you would need to do,
15 (b) Type [B]syslinux -sf /dev/sd[COLOR=#ff0000]x
[/COLOR][/B]     Code:
     syslinux -sf /dev/sdx 

at this point the command [B]syslinux -sf /dev/sdb1

creates a file called ldlinux.sys

I tried to boot from that point, but I get an error message saying "Error loading operating system"


For the files that you gave me, do I copy them to the root of my flash drive, that's where I copied them?

[/B]** I really do appreciate all your help Herman :) I am so close to getting this working**

---

### Post by Herman on 2007-11-29
>  For the files that you gave me, do I copy them to the root of my flash drive, that's where I copied them? Yes, you copy them to the ubuntu 710 partition (in the flash drive) and unzip them simultaneously with the command given in the how-to.
Quoted from the how-to:
> 20 Type **unzip -o -d /media/ubuntu710/ U710fix.zip**```
unzip -o -d /media/ubuntu710/ U710fix.zip
```Actually, I have already lent my USB with the persistent Ubuntu CD installation in it to a friend to try out Ubuntu 7.10 with, so I can't easliy take a look at mine right now to see if it has a file calledldlinux.sys but that's probably okay I guess.
If you still have trouble I have another USB stick here I can use to run through the how-to again to see what's going on.

I think I had that "Error loading operating system" error myself at one stage too, I think it happened after I moved the partition with GParted. All I had to do was re-install Syslinux because it probably works by sector numbers or block numbers to find its files.  When booting with GRUB, which understands file systems, we can move our partitions around without any problems. I'm just guessing that might have been my problem. Anyway, simply re-installing Syslinux fixed it.

Regards, Herman  :)

---

### Post by tech9 on 2007-11-29
> **Herman said:**
> Yes, you copy them to the ubuntu 710 partition (in the flash drive) and unzip them simultaneously with the command given in the how-to.
Quoted from the how-to:
```
unzip -o -d /media/ubuntu710/ U710fix.zip
```Actually, I have already lent my USB with the persistent Ubuntu CD installation in it to a friend to try out Ubuntu 7.10 with, so I can't easliy take a look at mine right now to see if it has a file calledldlinux.sys but that's probably okay I guess.
If you still have trouble I have another USB stick here I can use to run through the how-to again to see what's going on.

I think I had that "Error loading operating system" error myself at one stage too, I think it happened after I moved the partition with GParted. All I had to do was re-install Syslinux because it probably works by sector numbers or block numbers to find its files.  When booting with GRUB, which understands file systems, we can move our partitions around without any problems. I'm just guessing that might have been my problem. Anyway, simply re-installing Syslinux fixed it.

Regards, Herman  :)

After I copied the U710fix.zip from my desktop to /media/ubuntu710,

I ran this command

unzip -o -d /media/ubuntu710/ U710fix.zip

and got this...
unzip:  cannot find or open U710fix.zip, U710fix.zip.zip or U710fix.zip.ZIP.

I noticed step 18 says to [B]cd /home/ubuntu
[/B]
there is no directory called ubuntu directly under the home folder.
Should I make this through  the root account... I don't really think this part matters

what do you think?

---

### Post by Herman on 2007-11-29
>  I ran this command
unzip -o -d /media/ubuntu710/ U710fix.zip
and got this...
unzip:  cannot find or open U710fix.zip, U710fix.zip.zip or U710fix.zip.ZIP.
I noticed step 18 says to **cd /home/ubuntu** Yes, because before that the how-to had you cd'ed into the /cdrom directory while you were copying all the files from the CD to the USB partition. 
I think they really mean you should cd to your /home/username directory. 
Your /home/tech9 directory is the one that should have your U710fix.zip file in it.
If the file is located on your Desktop or some other folder, you need to move it to your /home/tech9 directory and then run the command and it should work.

EDIT: Well, for me it's cd /home/herman  , or just cd   because I'm working from my hard-disk-installed Ubuntu operating system. 
I guess the how-to was made for people who don't have Ubuntu installed to hard disk and maybe don't intend to, so they presume we're working from the Live CD, so cd /home/ubuntu would be correct in that case, or just cd would do.

Regards, Herman :)

---

### Post by Herman on 2007-11-29
> After I copied the U710fix.zip from my desktop to /media/ubuntu710, Oh, now I see what's wrong...
"***After*** I copied the U710fix.zip from my desktop to /media/ubuntu710,.. I ran this command "unzip -o -d /media/ubuntu710/ U710fix.zip."

Sorry, I didn't spot that right away.

You don't copy your U710fix.zip file to your /media/ubuntu710, you leave it in your /home/username folder and *use the command* to copy it and unzip it simultaneously. :)

I think that 's where you are getting confused.

Regards, Herman :)

---

### Post by Herman on 2007-11-29
Quoted from your post #31:
>  at this point the command [B]syslinux -sf /dev/sdb1
creates a file called ldlinux.sys
I tried to boot from that point, but I get an error message saying "Error loading operating system"[/B]
I made myself another USB flash memory disk with Ubuntu 7.10 in it according to the how-to and it does have a file called Idlinux.sys inside it.

---

### Post by brokenbones on 2007-11-30
I am jumping in again, since one of the suggestions I found here didn't work for me.

> 15 Type syslinux -sf /dev/sdx1 
That would install syslinux to the first sector of the ubuntu710 partition, to install syslinux to the MBR of the USB disk, you would need to do,
15 (b) Type syslinux -sf /dev/sdx
Code:
syslinux -sf /dev/sdx 

at this point the command syslinux -sf /dev/sdb1


According to the pendrivelinux directions, I placed syslinux on /dev/sdb[COLOR="Red"]1[/COLOR], and since my second partition (casper-rw) could not be mounted at boot, I tought syslinux should be installed on /dev/sdb as suggested in the quote above.

Unfortunately, when I try to place syslinux on sdb, I get a message telling me that no valid FAT system was found on that location. Why is that ? I didn't know I needed a file system to write a bootloader to an MBR... 

What am I doing wrong ?

TIA,

---

### Post by Herman on 2007-11-30
> According to the pendrivelinux directions, I placed syslinux on /dev/sdb[COLOR=Red]1[/COLOR], and since my second partition (casper-rw) could not be mounted at boot, I tought syslinux should be installed on /dev/sdb as suggested in the quote above.

Unfortunately, when I try to place syslinux on sdb, I get a message telling me that no valid FAT system was found on that location. Why is that ? I didn't know I needed a file system to write a bootloader to an MBR... Yes, I got that error too, I suppose it's because syslinux is designed to be a very small bootloader, good for certain jobs when used for what it is designed for.
It does seem as if Syslinux is designed for installing to the first sector of a FAT16 or FAT32 file system only. 
I'm sorry for making the mistake of saying you can install it to MBR, I was wrong, I edited the post #29 to say so as soon as I found out.

I don't know why the casper-rw file system won't automount either, when I made my new Gutsy persistent usb disk I ran into that problem too, but I have other computers here I can try, so I just tried it in a different computer and it mounted okay. I don't know why, they are all running up to date Gutsy Gibbon operating systems. One computer consistently refused to mount the casper-rw and the other computer had no problems. :confused:

Regards, Herman  :)

---

### Post by brokenbones on 2007-11-30
Unfortunately the same happens on 3 different computers

- IBM/Lenovo T43p, 1.86 Dothan CPU
- Homemade ASUS P5B, Core Duo E6600
- Homemade MSI 865PE, P4 2.6 (Northwood)

I tried to make the installation on all 3 computers, and using 2 different USB sticks, with the same result. The USB stick was plugged directly in the USB ports, not through a USB hub. 

Interestingly, the same error occurs when installing Pendrivelinux and making the ext2 partition for saving persistent changes. This second partition can't be mounted when booting from the USB stick, but partitions are normal when looked at in another Linux session.

I tried only 4GB sticks, maybe I should try another size. Or I should take my sticks to works and try them there (and get the boot in the worst of cases...)

Could anyone suggest maybe another distro with decent WLAN adapter support and persistent USB mode possibilities ?

TIA,

---

### Post by tech9 on 2007-11-30
> **Herman said:**
> Quoted from your post #31:

I made myself another USB flash memory disk with Ubuntu 7.10 in it according to the how-to and it does have a file called Idlinux.sys inside it.

so this is the file that should make the device bootable then. I am going to start over from formatting the drive sdb1 as fat and take it from there. I will keep you posted.

---

### Post by tech9 on 2007-11-30
> **brokenbones said:**
> and since my second partition (casper-rw) could not be mounted at boot,

Did you try my suggestion with gparted?... it sounds like your second partition is not formatted. You will know this is the case when you go into gparted and see that the format of the partition says unknown.

---

### Post by Herman on 2007-11-30
> so this is the file that should make the device bootable then. I am going to start over from formatting the drive sdb1 as fat and take it from there. I will keep you posted. Probably it would be a little bit more complicated than just that file to make the device bootable, but yes, it appears as if that file does have something to do with it, I'm not sure what exactly. I tried to open it already to take a look, but I don't know what software created it.
Good luck with it anyway, if you follow that tutorial well you should be successful, or if you know what you are doing you can take a few shortcuts and still be successful.
 Regards, Herman :)

---

### Post by tech9 on 2007-11-30
> **Herman said:**
> Probably it would be a little bit more complicated than just that file to make the device bootable, but yes, it appears as if that file does have something to do with it, I'm not sure what exactly. I tried to open it already to take a look, but I don't know what software created it.
Good luck with it anyway, if you follow that tutorial well you should be successful, or if you know what you are doing you can take a few shortcuts and still be successful.
 Regards, Herman :)

I beleive I maybe having some problems with my CD-ROM drive...

when I run this command...
cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz /media/ubuntu710/

I am getting this...

cp: cannot stat `casper': No such file or directory
cp: cannot stat `disctree': No such file or directory
cp: cannot stat `dists': No such file or directory
cp: cannot stat `install': No such file or directory
cp: cannot stat `pics': No such file or directory
cp: cannot stat `pool': No such file or directory
cp: cannot stat `preseed': No such file or directory
cp: cannot stat `.disk': No such file or directory
cp: cannot stat `isolinux/*': No such file or directory
cp: cannot stat `md5sum.txt': No such file or directory
cp: cannot stat `README.diskdefines': No such file or directory
cp: cannot stat `ubuntu.ico': No such file or directory
cp: cannot stat `casper/vmlinuz': No such file or directory
cp: cannot stat `casper/initrd.gz': No such file or directory

and this is after creating a brand new LiveCD of 710
...
update
I had to run the commands cd /cdrom and its working/copying files
*******************
cool my first cup of ubuntu foam coffee \\:D/

---

### Post by tech9 on 2007-11-30
Well Herman,

I tried steps 8 through 20 all over again line for line copy and paste...

This time step 20 was successful

 unzip -o -d /media/ubuntu710/ U710fix.zip

Archive:  U710fix.zip
  inflating: /media/ubuntu710/syslinux.cfg  
  inflating: /media/ubuntu710/isolinux.txt  

so thrilled, I restarted my PC and booted from USB and still got the error message

"Error loading Operating System"

I tried another computer... same message
I tried reverting back to 704 and making the pen-drive bootable 
through windows and could not.

I am getting a little closer to getting this working each time, I would hate to give up now.

It's got to be something small that is missing here

I will be persistent.

BTW.. Thank you for all of your help Herman :)

---

### Post by Herman on 2007-11-30
Try chainloading it from GRUB.

Since Syslinux isn't able to be installed in the USBdisk's MBR, you will be chainloading the boot sector of your ubuntu701 partition.

So from   [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 you would maybe type something like 'root (hd    ...(press tab)'

then if it answers '(hd0) (hd1), you would type 'root (hd0,   ...(and press tab again).

If it offers you a selection of partitions that look like your hard disk, try 'root (hd1,   (and press tab again.

Now, presuming your USBdisk's ubuntu710 partition is the first partition in your USb disk, you would do:
root (hd1,0)
chainloader +1
boot

...and your syslinux shuld show a menu with teh Ubuntu splash screen behind it. :)
And you can boot! 

I was only guessing those partition numbers, but you can confirm those with your own GRUB Command Line Interface, don't be afraid to replace what I have given here as an example with whatever is needed for your particular situation.

Regards, Herman :)

---

### Post by Herman on 2007-11-30
Be sure to copy down whatever commands and partition numbers you use to chainload syslinux in your USbdisk from your installed GRUB, so you can edit your /boot/grub/menu.lst file to make booting the USB disk easier in the future.

Otherwise, I think you can also install LiLo to teh MBR in the USbdisk, I think it tells you that at the end of the how-to we were following. I should read that part again and check up on that.
Like I said before, I used Super Grub Disk for USB in my first Ubuntu-in-USBdisk, so it boots from the MBR okay.

My latest USbdisk doesn't have that, so I guess I could test installing LiLo.
Or perhaps I could even install GRUB with the casper-rw ext3 partition doubling as a dedicated GRUB partition, I wonder if that would work? I will have to test that soon I just need a little snooze first though, I have been awake all night and it's almost morning here.
I'll be back in a while,...

Regards, Herman :)

---

### Post by tech9 on 2007-11-30
> **Herman said:**
> Be sure to copy down whatever commands and partition numbers you use to chainload syslinux in your USbdisk from your installed GRUB, so you can edit your /boot/grub/menu.lst file to make booting the USB disk easier in the future.

Otherwise, I think you can also install LiLo to teh MBR in the USbdisk, I think it tells you that at the end of the how-to we were following. I should read that part again and check up on that.
Like I said before, I used Super Grub Disk for USB in my first Ubuntu-in-USBdisk, so it boots from the MBR okay.

My latest USbdisk doesn't have that, so I guess I could test installing LiLo.
Or perhaps I could even install GRUB with the casper-rw ext3 partition doubling as a dedicated GRUB partition, I wonder if that would work? I will have to test that soon I just need a little snooze first though, I have been awake all night and it's almost morning here.
I'll be back in a while,...

Regards, Herman :)

I may look into the Lilo option at the end of the article... I am not that familiar with chainloading grub... I will read up on that too.
Does chainloading mean it will only boot from my linux box and no other computers?

Sleep well Herman :cool:

---

### Post by Herman on 2007-11-30
Thanks, I slept already, I'm awake agian now! :)
>  Does chainloading mean it will only boot from my linux box and no other computers? You will be able to chainload your USB disk from any computer that has GRUB in it and which supports booting a USB device.
 You will find that a lot of computers won't support booting a USB at all, even if they do have GRUB. I have some old computers like that and my newest computer is like that too. The BIOS wasn't designed for booting a USB, there's nothing that can be done about that.
However, if you want to boot in computers that don't have GRUB, that's easy to fix, you can use a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") to boot anything with! So you can have a Super Grub Disk CD, boot the computer with the CD and as soon as your Super Grub Disk CD is running, use that to boot your USB disk! :)

Or, you can use a super Grub Floppy Disk, or, you can do what I did and build your Ubuntu 710 persitent USB on top of[ Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb"). That's what I did with my first try at making a Ubuntu710 persistent USB.

This time I will try out something different.

The article says this at the end of it,
> **Note:** If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type **sudo apt-get install lilo** then type **lilo -M /dev/sd[COLOR=#ff0000]x[/COLOR]** (replacing **[COLOR=#ff0000]x[/COLOR]** with the letter of your flash device) I don't know why they say 'your memory may have a *corrupted* MBR'. As far as I know the partition table is alright, and no boot loader has been installed to MBR in my USB drive yet. I think they mean an *empty* MBR.

Well now I think we have probably install LiLo, as they instruct, or GRUB or even possibly some other boot loader or manager there.

The instructions are already there for installing LiLo, they look simple enough.
I'll try that first and let you know what happens. :)

---

### Post by cwill747 on 2007-11-30
I'm looking forward to trying this and using it at school... nice input guys.

---

### Post by tech9 on 2007-11-30
> **Herman said:**
> Thanks, I slept already, I'm awake agian now! :)
 You will be able to chainload your USB disk from any computer that has GRUB in it and which supports booting a USB device.
 You will find that a lot of computers won't support booting a USB at all, even if they do have GRUB. I have some old computers like that and my newest computer is like that too. The BIOS wasn't designed for booting a USB, there's nothing that can be done about that.
However, if you want to boot in computers that don't have GRUB, that's easy to fix, you can use a [Super Grub Disk]("http://sgd.benjamin-butschko.de/") to boot anything with! So you can have a Super Grub Disk CD, boot the computer with the CD and as soon as your Super Grub Disk CD is running, use that to boot your USB disk! :)

Or, you can use a super Grub Floppy Disk, or, you can do what I did and build your Ubuntu 710 persitent USB on top of[ Super Grub Disk for USB]("http://sgd.benjamin-butschko.de/?section=download#usb"). That's what I did with my first try at making a Ubuntu710 persistent USB.

This time I will try out something different.

The article says this at the end of it,
 I don't know why they say 'your memory may have a *corrupted* MBR'. As far as I know the partition table is alright, and no boot loader has been installed to MBR in my USB drive yet. I think they mean an *empty* MBR.

Well now I think we have probably install LiLo, as they instruct, or GRUB or even possibly some other boot loader or manager there.

The instructions are already there for installing LiLo, they look simple enough.
I'll try that first and let you know what happens. :)

Good Morning Herman!

I tried  lilo -M /dev/sdb1
and got this...
Fatal: /dev/sdb1 is not a master device with a primary partition table
 I also tried your suggestion with GRUB
root ...
......
boot

and it still did not work for me.

I am familiar with super grub disk... I actually have the ISO, I am going to make a disk and try that.

As a side note... I was able to load linux mint on my flash drive through windows and it boots juts fine, so I can rule out any physical problems with my drive. But, I would prefer ubuntu over linux mint + I couldn't get linux mint to be persistent either.

I like your idea of creating a third partition and installing Grub on it so the drive will be bootable. :)

let me know how that goes.

---

### Post by tech9 on 2007-11-30
> **cwill747 said:**
> I'm looking forward to trying this and using it at school... nice input guys.

Thanks! but most Thanks goes to Herman on this... he has helped me out quite a lot...
I hope to resolve my issues so that I can post for all to see and not have struggles making a bootable pen-drive like I have thus far.

---

### Post by Herman on 2007-11-30
```
herman@amd46b:~$ sudo lilo -M /dev/sdd
[sudo] password for herman:
Backup copy of /dev/sdd in /boot/boot.0830
The Master Boot Record of  /dev/sdd  has been updated.
herman@amd46b:~$ 

``` You know, I can't see how this will work, hiow is LiLo going to boot with only the MBR part of it installed? There needs to be two parts of LiLo, and Grub comes in three parts. The stage1 part that fits in the MBR won't do anything by itself. Oh well, I'll try it anyway....

Ah, I see, as long as the USB had an MBR, you can just set the ubuntu710 partition as active, (set the 'active' flag in the partition table on it), and the BIOS will go to the bootsector of that partition and boot syslinux without any boot manager at all. :)

So what I did was boot my hard disk installed GRUB and find the USB disk's hard drive number and the partiion number for ubuntu710 the same way I already described.
Then I typed,
```
root (hd1,0)
makeactive  #this command tells GRUB to set the active flag (boot flag) on the partition for me
chainloader +1
boot
```From now on the USb disk should boot up okay from its own MBR, because the active flag will stay there unless I move it myself some day.

...well I just tested it on another different computer. It's a lot slower to boot up in another computer with different hardware, I imagine it has to configure itself for the different hardware, but at least it does that automatically, I don't need to run 'sudo dpkg-reconfigure xserver-xorg'.

I booted in a computer that doesn't have GRUB, (it's one I have here with a Windows virus to see if I can fix it for someone), and it couldn't boot the USB by the F8 or F12 keys, so I used my Super Grub Disk CD and I didn't need the 'makeactive' command anymore, indicating it would boot without the Super Grub Disk CD if I had another computer that could boot from the F8 or F12 keys. Here's how it might work in some computers: [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key")

Installing LiLo has nothing to do with it though, that's just silly. 
Setting the boot flag is all you need to do. You can do that with any partition editor or any advanced boot loader. GParted Partition Editor will do it for you, or Super Grub Disk can easily do that too.

Regards, Herman :)

---

### Post by Herman on 2007-11-30
```
 I tried  lilo -M /dev/sdb1
and got this...
Fatal: /dev/sdb1 is not a master device with a primary partition table
 I also tried your suggestion with GRUB
root ...
......
boot
```  lilo -M /dev/sdb would have worked in your case.

If you used /dev/sdb in that command it would direct LiLo to install in the USBdisk's MBR, 

You have used /dev/sdb1 in the command which would be trying to install Lilo in your first partition's boot sector, that's the one you installed syslinux to ins't it?
I hope that didn't overwrite syslinux! I don't think so, it looks like it just gave you an error message. If it did it wouldn't matter, just install syslinux again.

You're almost there !

Regards, Herman :)

---

### Post by tech9 on 2007-11-30
> **Herman said:**
> ```
 I tried  lilo -M /dev/sdb1
and got this...
Fatal: /dev/sdb1 is not a master device with a primary partition table
 I also tried your suggestion with GRUB
root ...
......
boot
```  lilo -M /dev/sdb would have worked in your case.

If you used /dev/sdb in that command it would direct LiLo to install in the USBdisk's MBR, 

You have used /dev/sdb1 in the command which would be trying to install Lilo in your first partition's boot sector, that's the one you installed syslinux to ins't it?
I hope that didn't overwrite syslinux! I don't think so, it looks like it just gave you an error message. If it did it wouldn't matter, just install syslinux again.

You're almost there !

Regards, Herman :)

Hi Herman! :)

I got it working \\:D/

What's really weird though, is that I didn't do anything different other than repeating steps 8 through 20 again.

at that point, I wanted to boot up with super grub to analyze the partitions...
but to my amazement, my flash drive booted ubuntu 7.10
I have tested this and it is persistent - all of my changes were saved :)

Thank you so much for all of your help Herman...

I will keep playing with this, but I think I worked out the major problems.

---

### Post by Herman on 2007-11-30
Okaaay !!! :guitar:

Good work there, tech9!
Congratulations! :)

Regards, Herman :)

---

### Post by brokenbones on 2007-12-02
> **tech9 said:**
> Did you try my suggestion with gparted?... it sounds like your second partition is not formatted. You will know this is the case when you go into gparted and see that the format of the partition says unknown.

It is formatted and labeled. Gparted sees it as an ext2 partition, but the partition is listed with an exclamation mark. The properties tab tells me there is no mounting point, and when I try to edit or mount the partition, gparted crashes.

As I mentionned earlier I think, if I start a session from the LiveCD and then plug in my USB stick, both partitions on the stick are present and contain data. When I boot from the stick itself, the second partition cannot be mounted.

I guess I'll have to try one more different USB stick after all, or another boot loader than syslinux.

---

### Post by kelvin spratt on 2007-12-02
Gutsy 7.10 works on pen drive flawlessly its all to do with setting up and installing use Gparted live to partition use this link, [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)
i used a 2gb stick with the first partition 850mb fat16 and bootable the rest I formated to ext2. You then need to run the live Live Cd. insert the flash drive. Open the terminal  type **sudo su. then **Type **fdisk -l **to list available drives/partitions. Note which device is your flash drive (example: **/dev/sda**) Throughout this tutorial, replace [COLOR=#ff0000]**x**[/COLOR] with your flash drive letter. For example, if your flash drive is **sdb**, replace [COLOR=#ff0000]**x**[/COLOR] with **b**. skip the next bits. and start at[LIST=1]
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]1** to ensure the 1st partition is unmounted
[*]Type **mkfs.vfat -F 16 -n ubuntu710 /dev/sd[COLOR=#ff0000]x[/COLOR]1** to format the first partition
[*]Type **umount /dev/sd[COLOR=#ff0000]x[/COLOR]2** just to ensure the 2nd partition is unmounted
[*]Type **mkfs.ext2 -b 4096 -L casper-rw /dev/sd[COLOR=#ff0000]x[/COLOR]2 **to format the second partition
[*]Remove and Re-insert your flash drive
[*]Back at the terminal, type **apt-get update**
[*]Type [B]apt-get install syslinux mtools
[/B]
[*]Type **syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1**
[*]Type **cd /cdrom**
[*]Type **cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz ****casper/initrd.gz ****/media/ubuntu710/**[INDENT]Ignore any **"cannot create symbolic link" **errors
[/INDENT]
[*]Type **cd /home/ubuntu**
[*]Type **wget pendrivelinux.com/downloads/U710fix.zip**
[*]Type **unzip -o -d /media/ubuntu710/ U710fix.zip**
[*]Restart your computer, set your BIOS or Boot menu to boot from the USB device and reboot again.[/LIST]You should now have a USB Ubuntu 7.10 Gutsy Gibbon flash drive that should automatically save your changes, restoring them on boot.
 **Note:** If your having trouble getting Ubuntu to boot, your [[COLOR=#0066ff][COLOR=#0066FF ! important][FONT=&quot][COLOR=#0066FF ! important][FONT=&quot]memory [/FONT][/FONT][/COLOR][FONT=&quot][COLOR=#0066FF ! important][FONT=&quot]stick[/FONT][/color][/FONT][/color][/color]]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/#") may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type **sudo apt-get install lilo** then type **lilo -M /dev/sd[COLOR=#ff0000]x[/COLOR]** (replacing **[COLOR=#ff0000]x[/COLOR]** with the letter of your flash device)

I've done this several times now I had trouble getting it right the first time but now works every time

---

### Post by schmildo on 2007-12-02
I've been having problems getting it working, I'm a bit concerned about the step where you copy files from the CD to the 'ubuntu710' partition. The guide says to ignore the symlink errors(I get two), but i'm also getting these errors:

cp: cannot stat `disctree': No such file or directory
cp: cannot stat `ubuntu.ico': No such file or directory

And the errors seem justified; There is no folder called disctree in the root of the cd, and there is no ubuntu.ico file either. I checked I have the i386 version, and i've confirmed the Md5 checksum, and i also checked the cd for errors when I booted from it, so it shouldnt be a problem with my ISO.

I'm going to ignore these errors (again) and try a third time to do this. Last time I got an error on bootup that said: "cannot find kernel:linux"

---

### Post by schmildo on 2007-12-02
Oh yeah, and gparted crashes all the time. It will always crash for example, when I try to use the label feature. It also crashed when I tried to reformat the first partition to fat16 .(because for some reason I had the exclamation point icon appearing... i originally thought that was just because it wouldnt read the label which is normal... but when i looked at the details it said it couldnt read the filesystem, after i formatted it to fat16 again, it crashed, but i went back in and the error had gone.)

---

### Post by schmildo on 2007-12-02
Well I'll be a monkey's infested left foot! It worked, and I'm not sure what i've done differently. I'm fairly sure that for me to get it going, I had to follow the instructions, but at some point check in gparted to see if there is an error reading the fat16 partition, reformat it to fat16 in gparted, and then continue with the instructions.

I'm booting from my bios using the USB-HDD option instead to USB-CD.

It takes 2mins and 24 seconds from the audio beep at POST to get into the desktop.
(The moment I get in the monitor shuts off so I have to hit a key)

There is one thing that is bothering me, when I was booting into edgy eft via CD and persistent USB, the USB wasn't visable on the desktop if I was in persistent mode. But now, with Gibbon, i'm booting straight from the USB with no CD, and it's running in persistent mode (i've tested this) but I can see both the 'ubuntu710' and 'casper-rw' partitions on teh desktop?

Is this a problem?

---

### Post by kelvin spratt on 2007-12-03
I did say use Gparted live cd for partitioning not the ubuntu live cd. Gparted Live CD will unmount all the drives and does not crash. the Ubuntu live CD does crash for some reason I think its got a bug, thats the reason for using THE GPARTED LIVE CD.

---

### Post by tech9 on 2007-12-03
> **brokenbones said:**
> It is formatted and labeled. Gparted sees it as an ext2 partition, but the partition is listed with an exclamation mark. The properties tab tells me there is no mounting point, and when I try to edit or mount the partition, gparted crashes.

As I mentionned earlier I think, if I start a session from the LiveCD and then plug in my USB stick, both partitions on the stick are present and contain data. When I boot from the stick itself, the second partition cannot be mounted.

I guess I'll have to try one more different USB stick after all, or another boot loader than syslinux.

ok, good idea... try another USB stick and see if you are encountering the same errors. If not, you can pretty much isolate the problem to your other flash drive.

---

### Post by tech9 on 2007-12-03
> **Herman said:**
> Okaaay !!! :guitar:

Good work there, tech9!
Congratulations! :)

Regards, Herman :)

Thanks Again Herman! 

YOU ARE THE MAN =D>

Tech9 :)   

:guitar:

---

### Post by Monstroxus on 2007-12-04
I installed Gutsy without any problems using the pendrivelinux's site instructions. (can be done within 20 minutes or so)... it saves settings, it works nicely until I install the extensive compiz manager. Initially everything runs perfectly after installing it, however upon shutting down and rebooting the USB install is screwed. A pity because the extensive effects are so nice... the cube and such...

---

### Post by tech9 on 2007-12-05
> **Monstroxus said:**
> I installed Gutsy without any problems using the pendrivelinux's site instructions. (can be done within 20 minutes or so)... it saves settings, it works nicely until I install the extensive compiz manager. Initially everything runs perfectly after installing it, however upon shutting down and rebooting the USB install is screwed. A pity because the extensive effects are so nice... the cube and such...

that's good to know... thanks for the post.

---

### Post by brokenbones on 2007-12-10
Well well,

Time to report back I am afraid. So I tested 2 more 4GB USB flashdrives, with the same result. Installed from the Ubuntu 7.10 LiveCD to the memory stick according to Pendrivelinux, but when booting from the freshly installed USB flashdrive, the "casper-rw" partition cannot be mounted, and no persistent changes can be made.

When I boot again from the LiveCD (or another Linux session) and plug in the flashdrive, no errors are reported on either partition of the USB drive. I redownloaded the LiveCD, tried the install on 3 different computers with 3 different sticks, always with the same result. Frustrating  :(

I am about to give up, unless someone comes up with a brilliant suggestion...

---

### Post by tech9 on 2007-12-11
> **brokenbones said:**
> Well well,

Time to report back I am afraid. So I tested 2 more 4GB USB flashdrives, with the same result. Installed from the Ubuntu 7.10 LiveCD to the memory stick according to Pendrivelinux, but when booting from the freshly installed USB flashdrive, the "casper-rw" partition cannot be mounted, and no persistent changes can be made.

When I boot again from the LiveCD (or another Linux session) and plug in the flashdrive, no errors are reported on either partition of the USB drive. I redownloaded the LiveCD, tried the install on 3 different computers with 3 different sticks, always with the same result. Frustrating  :(

I am about to give up, unless someone comes up with a brilliant suggestion...

Hi  				Lorenzo Sandini

when you plug the flash drive in to your regular ubuntu OS does it find both /dev/sdb1 and /dev/sdb2? If it does not load/mount /dev/sdb2 then you need to make sure that it is formatted correctly. I had the same problem as you. When I formatted the /dev/sdb2 with gparted  as ext2. The drive automatically loaded/mounted.

---

### Post by kelvin spratt on 2007-12-11
brokenbones
Did you install in linux or windows?  Linux installs correctly once you have got it right. It took me several attempts to install correctly but now its simple a matter of mins. By the way I use SanDisk cruzer micro 4gb.

---

### Post by tech9 on 2007-12-12
> **kelvin spratt said:**
> brokenbones
Did you install in linux or windows?  Linux installs correctly once you have got it right. It took me several attempts to install correctly but now its simple a matter of mins. By the way I use SanDisk cruzer micro 4gb.

@brokenbones...

I agree with kelvin spratt, it took me several attempts to get it working. don't give up... persistence pays :)

---

### Post by phash69 on 2007-12-12
I am having a problem with installing Ubuntu 7.10 onto a flash drive. I follow the instruction exactly from [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install)
Everything comes up exactly as it should and when i finally boot from the flash drive it tells me that it cannot find the linux boot. I have also ran lilo like the site suggested and that did not seem to work. Any help would be greatly appreciated.  I should also note that I am an incredible n00b.

---

### Post by tech9 on 2007-12-12
> **phash69 said:**
> I am having a problem with installing Ubuntu 7.10 onto a flash drive. I follow the instruction exactly from [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install)
Everything comes up exactly as it should and when i finally boot from the flash drive it tells me that it cannot find the linux boot. I have also ran lilo like the site suggested and that did not seem to work. Any help would be greatly appreciated.  I should also note that I am an incredible n00b.

One critical command to run is 
[B]syslinux -sf /dev/sd[COLOR=#ff0000]x[/COLOR]1
This makes it bootable
[/B]

---

### Post by phash69 on 2007-12-12
I just ran through the entire process again and get the same error message on boot.  Cannot Find Linux Kernal: Linux Boot:

---

### Post by phash69 on 2007-12-12
Ok i ran through it again and I realized i was getting a fatal error on the liloconfig.  It tells me that I need to repair or hand-roll my own /etc/lilo.conf.  What does this mean?  Is there a fix?

---

### Post by tech9 on 2007-12-12
> **phash69 said:**
> Ok i ran through it again and I realized i was getting a fatal error on the liloconfig.  It tells me that I need to repair or hand-roll my own /etc/lilo.conf.  What does this mean?  Is there a fix?

I would boot with grub personally, like herman told me "stay away from lilo" It is very important that all steps are executed correctly... in order for this to work. I tried skipping some steps and ran into some similar errors. what exactly did your error say?

---

### Post by monroetransfer on 2007-12-14
"Error loading operating system."

Damnit.

I can't boot from my hard drive, from either cd drive, or apparently from usb. Please, this is my only option, isn't it? I can't even get dban to work properly on my other usb. Is there a step by step guide to installing usb dban? because it gives me: "Error: do you want to try again [yes|no]" Do i need to format my usb a specific way?

HELP ME PLEASE SOMEBODY

---

### Post by tech9 on 2007-12-14
> **monroetransfer said:**
> "Error loading operating system."

Damnit.

I can't boot from my hard drive, from either cd drive, or apparently from usb. Please, this is my only option, isn't it? I can't even get dban to work properly on my other usb. Is there a step by step guide to installing usb dban? because it gives me: "Error: do you want to try again [yes|no]" Do i need to format my usb a specific way?

HELP ME PLEASE SOMEBODY

I understand that you are frustrated, but cursing will only make the situation worse.  In cases when I run in to problems, the first step I take is to calm down if I feel that I am getting frustrated/angry. Remember every problem has a solution, you just need to find it.

Now, to address your issue. I would start from scratch. Try to backup any files through liveCD then reinstall clean. If your liveCD does not even boot up, Then see if you cannot burn another CD as an ISO image. If you only have one computer, try to find another source to do so. 

Once you have a bootable Ubuntu OS, then try to execute all these steps to create a bootable USB Drive....

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Good Luck & let me know if you run across anymore problems. :)

---

### Post by brokenbones on 2007-12-17
Hello all and thanks for your help and suggestions,

I think I am done with trying. I tried the various install methods from the ubuntu wiki and pendrivelinux, and your suggestions too. I just can't get the persistence feature to work with my "Ubuntu on a stick" install.

I formatted the USB flashdrive using the Gparted LiveCD and noticed it left some unused space between the first FAT partition and the ext2 partition, unlike fdisk. However, even though my USB stick is partitioned correctly, (I see all partitions when I test the stick in another linux environment), and independently of the method I use to partition and format it, the casper-rw partition just won't mount when booting from the USB stick itself.

This is rather depressing and frustrating, after all the hours spent trying. Thank you all anyway !

---

### Post by tech9 on 2007-12-17
> **brokenbones said:**
> Hello all and thanks for your help and suggestions,

I think I am done with trying. I tried the various install methods from the ubuntu wiki and pendrivelinux, and your suggestions too. I just can't get the persistence feature to work with my "Ubuntu on a stick" install.

I formatted the USB flashdrive using the Gparted LiveCD and noticed it left some unused space between the first FAT partition and the ext2 partition, unlike fdisk...

This is rather depressing and frustrating, after all the hours spent trying. Thank you all anyway !

your welcome for the help... I understand where you are coming from. I had the same problems before I got mine working. It is frustrating, but I have learned that being persistent pays...

That is very strange that you have some unused space left. If you are not completely set on giving up, my last suggestion would be to delete all partitions with gparted, even the partition that is unused to where you have no partitions left  and start over with the pen-drive site's exact instructions line by line, step by step.

---

### Post by monroetransfer on 2007-12-19
I've already created the bootable drive. I'm legitimately frustrated, but I didn't think that "damnit" was considered such a powerful oath among ubuntu forum users. Now that you know that I have some degree of knowledge with computers, can we put our heads together for a solution?

---

### Post by tech9 on 2007-12-20
> **monroetransfer said:**
> I've already created the bootable drive. I'm legitimately frustrated, but I didn't think that "damnit" was considered such a powerful oath among ubuntu forum users. Now that you know that I have some degree of knowledge with computers, can we put our heads together for a solution?

Did you try my suggestion? ...

"Now, to address your issue. I would start from scratch. Try to backup any files through liveCD then reinstall clean. If your liveCD does not even boot up, Then see if you cannot burn another CD as an ISO image. If you only have one computer, try to find another source to do so. 

Once you have a bootable Ubuntu OS, then try to execute all these steps to create a bootable USB Drive....

[http://www.pendrivelinux.com/2007/09...ibbon-install/]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")"

---

