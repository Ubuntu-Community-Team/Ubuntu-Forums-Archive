---
title: "Real install to USB on Ubuntu 10.10"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by applerock79 on 2011-03-21
I've used the STARTUP DISK CREATOR to install 10.10 to a thumbdrive.
It works, but I can't install any software or save any files to the desktop, that It'll remember. When I reboot, all my software I installed is gone.

2 Questions:
1. How can I install this to my 16gb USB stick so that it behaves exactly like a HD install?
2. Can I install this to my larger, 160gb USB Hard Drive in a similar manner?

In case your wondering, both my internal HD and HD controller on my laptop are shot. This is the reason for the install to USB, either to a thumbdrive or an external HD.

---

### Post by oldfred on 2011-03-21
A full install to a flash or external drive is really the same, the flash just needs a few extra setting to make it not quite as slow. Realize that USB ports are slow compared to hard drives and flash devices are slower than hard drives. It still is functional on a flash drive. What size flash drive - 4GB is very tight but has been done, 8GB or more is better.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by targets on 2011-03-21
i had the same installed from 2 different USB sticks but when i reboot theres nothing there ,no solution found

---

### Post by C.S.Cameron on 2011-03-21
With usb-creator you can select "Extra Space" to make drive persistent.

Step by step for a full install to Flash drive follows, adjust partition size as desired, for external HDD make first partition NTFS rather than FAT.




Check MD5SUM of the Ubuntu iso file.
Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
(Optional partition for use on Windows machine)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 400MB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 2.77GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 600MB, Beginning, Ext2, and Mount point = "/home" then OK.
(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by applerock79 on 2011-03-23
Thanks Cameron, I'll try that procedure.

---

### Post by applerock79 on 2011-03-30
Ok, tried that procedure.
Unplugged internal HD, since it is dead anyway.

Booted with Ubuntu CD as per instructions.

When I got to "place check mark next to check for 3rd party extensions and download updates" I could not do forward. Button was in phantom. (also an X on requires 2.6 gig of free space)

My USB 160gb HD was plugged in but not being recognized.

So, I tried to restart and just chose TRY UBUNTU.

Let it boot into desktop from cd, then plugged in USB HD.
It didn't recognize it. Tried several times.

I guess this is why the "Forward" button is greyed out. How do I get the Ubuntu CD to recognize my USB. (still no HD installed btw, my only HD is the external usb)

---

### Post by C.S.Cameron on 2011-03-30
Does your 160GB show up in BIOS?

---

### Post by applerock79 on 2011-03-30
Good question. Didn't think the BIOS would recognize USB P&P periphials, including ext HDs.

I've plugged the HD into another Win7 laptop & Ubuntu desktop, both recognize it fine.



It is a newer laptop, had Vista opn it.

---

### Post by Hedgehog1 on 2011-03-31
If your laptop offers USB 2.0 and USB 3.0 ports, you will need to plug the drive into a USB 2.0 port to be the boot drive.  For right now, Ubuntu cannot boot from USB 3.0 ports (they can be used for data drives just fine).

***The Hedge***

:KS

---

### Post by C.S.Cameron on 2011-03-31
> **applerock79 said:**
> Good question. Didn't think the BIOS would recognize USB P&P periphials, including ext HDs.

I've plugged the HD into another Win7 laptop & Ubuntu desktop, both recognize it fine.



It is a newer laptop, had Vista opn it.


Most newer computers will even see a flash drive as a hard drive.
If you have one try plugging it in and booting to BIOS, look at hard disk priority.

---

