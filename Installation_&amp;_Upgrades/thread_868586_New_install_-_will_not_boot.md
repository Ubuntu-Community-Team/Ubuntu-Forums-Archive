---
title: "New install - will not boot"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-07-24
I installed 8.4.1 server amd64. The install completed successfully, I removed the CD and restarted the computer. 

After the PC BIOS messages, I got a blank screen and a blinking cursor. That's all. No messages.

I have reinstalled dozens of times over 3 days and the result is the same every time. I have tried installing on different HDDs and with different options, but the result is always the same.

I had a previous version of Ubuntu installed on this hardware. I have not changed any hardware since, except for BIOS settings and RAID controller settings in my attempt to solve this issue.

I have an LSI MegaRAID 320E card and an ARC-1220 card. I tested once by removing the Areca card (the boot drive is on the LSI card) and that didn't make any difference.

This is tough to trouble shoot because all I get is a blank screen.

I have also tried letting it boot to the LiveCD and then selecting "boot from first hard drive" and all that does is give me the same result. The screen says "booting from local drive" and the cursor blinks, and that's it.

I have made sure I have the right logical disk set as the boot disk in the MegaRAID bios. I have a separate /boot partition on this logical disk and it has the bootable flag set. It is 300 MB. No other O/S is installed.

All other HDD partitions are encrypted (done during installation process).

What else can I check? How would you guys troubleshoot this? After 3 days, I'm out of ideas. Thanks.

EDIT: does it make any difference that I put the /boot partition at the end of the disk? This is one thing I have done consistently in all my installs. I make the 300 MB boot partition, specify "end" of drive, then I make the other partition (that will be encrypted) and use the rest of the disk space. Does it make any difference where the /boot partition is?

---

### Post by MountainX on 2008-07-24
bump

---

### Post by dstew on 2008-07-24
It should not matter that the /boot partition is at the end of the drive, unless you have an older BIOS that cannot read files beyong the 1024 cylinder limit. Your system is too new for that, I think.

From the behavior of the system it sounds like the boot loader is not being loaded by the BIOS, or once loaded, it is not running properly. It could be that it was mis-installed. I don't know about your RAID setup, but could it be that there is no boot loader in the MBR of the array (if you are booting an array)? Installing grub onto a FakeRaid is tricky. I am not aware that the Ubuntu installer is able to do this. The [FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto") has some info on installing to a fakeraid. I have set up a software RAID before, but have no hands-on experience with fakeraid.

Anyway, if you can set aside one disk as un-RAIDed, and put your /boot partition on it, and install grub to the MBR of that disk, you should be able to at least get grub to load. But if you are booting a RAIDed disk, you have to have used dmraid to install Ubuntu and grub in order to get it going.

---

### Post by MountainX on 2008-07-24
> **dstew said:**
> It should not matter that the /boot partition is at the end of the drive, unless you have an older BIOS that cannot read files beyong the 1024 cylinder limit. Your system is too new for that, I think.


Thank you. That's good to know.

> **dstew said:**
> 
Installing grub onto a FakeRaid is tricky. 

I'm actually not using FakeRaid or software raid. My controller handles the raid and it should be seamless to Ubuntu -- should be is the key phrase.

I actually just tested it with passthrough disks and I still wasn't able to resolve the problem...

---

### Post by dstew on 2008-07-25
I doubt that that controller is true hardware RAID. It probably needs some operating system software to run it. Typically, a fakeRAID controller will off-load the parity calculations to the OS (when using RAID-5, for example). True hardware RAID will do these calculations in an on-board processor.

In Ubuntu, that software is dmraid. To install Ubuntu on a "fakeRAID" controller, you need to install the dmraid program onto the Live CD system in order for the RAID to be used properly. See the [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto").

I could not prove to myself that the controller you have is fakeRAID, but I think it is based on your problem and on what I know generally about controllers.

---

### Post by MountainX on 2008-07-25
> **dstew said:**
> I doubt that that controller is true hardware RAID

The problem may be that I made a typo in my original post. 

I have an LSI MegaRAID 320-2E SCSI controller and an Areca ARC-1220 PCI-Express x8 SATA II Controller Card.

These are top of the line RAID controllers. Hardware RAID.

---

### Post by dstew on 2008-07-25
OK, I believe you. It seems that grub was mis-installed, or the BIOS is booting from a disk that does not have a boot loader installed, or the boot loader is corrupted. Boot a live CD and try to [re-install grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by MountainX on 2008-07-25
I have installed Ubuntu at least a dozen times, and I doubt I would get a corrupted install that may times in a row. 

I briefly tried Super Grub disk, and based on what I saw, my best guess (atm) is that Ubuntu doesn't see my HDDs in the same order that the BIOS sees them. Since they are all the same size/brand/model, I cannot tell which physical disk is which.

EDIT: if I remove all disks except one and install Ubuntu into 1 partition (no /boot partition), the install works.

---

### Post by dstew on 2008-07-25
A couple of thoughts. Does your BIOS boot a *disk* (an array in your case) or a *partition*? If it boots a partition, then grub has to be installed into the partition instead of the MBR. By default, the grub boot loader installs into the MBR of a disk, not a partition. So, if your BIOS is trying to boot a partition, but there is not boot loader there, you might get the behavior you see.

About the BIOS disk order, here is what I understand. When grub is installed, you are usually running from a CD operating system of some kind, the Live CD or alternate install CD. These CD operating systems are Linux systems, and it is Linux that detects the disks. So, grub gets installed to the disk that Linux thinks is (hd0). But the BIOS may enumerate the disks differently than Linux, so grub can get mis-installed this way. The device.map file stored in the /boot/grub directory shows how Linux saw the disks. This file is not used except when running grub-install from the operating system. Grub itself does not use device.map.

If you think that the BIOS is enumerating the disks differently, you can try several things. If you have a floppy drive, make a [grub boot floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") and boot it. Now you have grub running in a "native" environment, without the complications of the operating system. You can then use grub commands to figure out which disk is which, and install grub to the proper disk. Grub gets its enumeration from the BIOS, so if you are running from a floppy, and install grub from there, the enumeration should be correct.

To figure out which disk is which, you can use the auto-complete feature of grub to look for files, get directory listings etc. To get a listing of the root directory of (hd0), you can enter this on the grub> command line:
```
kernel (hd0)/
```then hit the <TAB> key. It should give you a list of the files in the root directory, in case you want to use one as a kernel. You can get drive geometry, or a list of avialable drives using the grub commands and the auto-complete feature. Type "help" on the grub command line to get a list of commands.

---

### Post by MountainX on 2008-07-25
Thank you! Very informative. 

> **dstew said:**
> A couple of thoughts. Does your BIOS boot a *disk* (an array in your case) or a *partition*?


I do not know. How would I find out?

> **dstew said:**
> 
If you think that the BIOS is enumerating the disks differently, you can try several things. If you have a floppy drive, make a [grub boot floppy]("http://www.gnu.org/software/grub/manual/grub.html#Creating-a-GRUB-boot-floppy") and boot it. 

I have a Super Grub CD that I can boot from. I assume that will accomplish the same thing as the floppy you suggested.

BTW, I'm installing the server edition.

I'm going to work on your suggestions. I'll report back. Thanks.

---

### Post by dstew on 2008-07-25
I suspect the SuperGrub CD boots a Linux system, so you might have the same problem you get with the grub shell, or grub-install programs running under Linux: you get the Linux enumeration, and not the BIOS enumeration. But, I am not familiar with the SuperGrub CD, so I can't say for sure.

---

### Post by MountainX on 2008-07-31
SOLVED

I simply set up my hardware so that I was not booting from the LSI MegaRAID controller. I'm booting from a WD Raptor connected to the motherboard SATA now, and that resolved everything very easily.

---

### Post by dstew on 2008-08-01
Thanks for the update.

---

### Post by MountainX on 2008-08-01
I found the ***explanation*** of my original problem here:

[http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM](http://tjworld.net/wiki/Linux/Ubuntu/HardyRAID5EncryptedLVM)

BTW, this is an excellent guide to how to setup passwordless disk encryption.

---

### Post by MountainX on 2009-03-02
It turns out that my solution was a bit fragile (because I really didn't fully understand the problem). When I changed the configuration slightly, the whole thing broke.

So I started a [new thread]("http://ubuntuforums.org/showthread.php?t=1080832") and learned a lot more about how to make Ubuntu boot on a system with a lot of disks.

---

