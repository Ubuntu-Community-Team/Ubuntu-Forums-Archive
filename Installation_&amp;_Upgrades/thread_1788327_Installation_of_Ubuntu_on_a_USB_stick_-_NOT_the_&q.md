---
title: "Installation of Ubuntu on a USB stick - NOT the &quot;Live CD on a stick&quot;"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by Odense on 2011-06-22
I would like to install Ubuntu on a (8 gb or 16 gb) USB stick.
I did start the process yesterday on my laptop running Ubuntu and booted on a Live CD- but stopped when I saw that I would get a boot menu.

I do not want a boot menu - (and I do not want the "persistant Live CD on a stick") I just want to be able to boot on the USB stick and be running a "normal" Ubuntu installation.

Is this possible and if it is - how do I do it ?

---

### Post by jerrrys on 2011-06-22
there are options

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by MooPi on 2011-06-22
This is possible but I have had best success doing this with the internal hard drive removed before proceeding. This eliminates the need to edit grub to allow for normal boot from the host computer.

---

### Post by Odense on 2011-06-22
Moopi - I don't like the persistent option - it is not really persistent enough and I don't like a default user.

Thanks jerrys - but there is too many options and choices there - too big a risk of screwing up my existing installation (on the HD) too - I would like the "for dummies" version - simple and as fail-safe as possible :D

---

### Post by jerrrys on 2011-06-22
you want safe?  remove/disconnect your hdd so that the only thing that can go wrong is the usb.  then just do a normal install to the usb.  this will also shorten the life of your usb...

---

### Post by C.S.Cameron on 2011-06-22
Step by step using a desktop, for laptop remove HDD:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by Odense on 2011-06-22
Thanks guys :)

jerrys - I will have to live with the shorter life span - hopefully not THAT short then it would be close to useless

C.S. Cameron - Thanks - that is detailed and safe - I guess I was hoping I could do safe without dismoutning the HD - but I guess it is only really safe that way

---

### Post by Brushstroke on 2011-06-22
Make it an ext2 instead of ext4 if you're going to do this. It's the journaling feature on ext3 and ext4 that mainly contribute to the shortening of the USB drive's lifespan.

---

### Post by oldfred on 2011-06-22
I regularly post links to another post where C.S.Cameron has his instructions. 

But I usually also post links to Herman's site as he includes screenshots and lots of detail, if you want to know more or understand the process.
An install to a Flash drive is not really different than any install to a second drive, but with some settings to reduce writes which greatly slow slow down on flash drives.
Any install to a second drive requires you to use manual partitioning, so you get the option to install grub2's boot loader to the external/flash drive.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

