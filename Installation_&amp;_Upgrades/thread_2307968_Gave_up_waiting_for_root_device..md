---
title: "Gave up waiting for root device."
date: 2015-12-29
forum: Installation &amp; Upgrades
---

### Post by erik37 on 2015-12-29
Hi! I just recently came across Ubuntu and wanted to download it to my Lenovo IdeaPad S415 Touch computer. I used a USB to download Ubuntu and everything worked fine until the installation phase. I had to manually create partitions, which I did through watching a YouTube video... and after the installation was "complete," I could not boot Ubuntu (and no longer have the option to boot Windows... R.I.P.).

Turning on my computer, I get the "GNU Grub" which has me select boot from either "*Ubuntu" or "Advanced options for Ubuntu (which has Ubuntu, with Linux 4.2.0-16-generic and recovery mode)" or "System Setup." Trying to launch the recovery mode Ubuntu (because the other two options freeze up or lead to nothing), I'm eventually taken to a screen which displays a bunch of information then says:

```
Gave up waiting on root device. Common problems: 

- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/cd2027bf-f666-430f-a614-2404b4c80409 does not exist.
Dropping to a shell!


Busybox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands. 

(initramfs) _

```

and from there I'm completely clueless as to how to get my computer to work again.

Extra info:
   Computer: Lenovo IdeaPad S415 Touch
   Processor - AMD A6 Quad-Core w/ integrated graphics
   RAM - 4GB
   Hard Drive - ~500GB
   SSD - N/A
   USB - 32GB SanDisk thingy

Typing "cat /proc/cmdline" produces the following:

```
BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-generic.efi.signed root=UUID=cd2027bf-f666-430f-a614-2404b4c80409 ro recovery nomodeset
```

Typing "sudo fdisk -l" gives an error "/bin/sh: sudo: not found" which means sudo isn't a command I would guess since it isn't listed as one... just going off what I read in other threads.

Please help! I don't mind what OS I end up with, but I'd like to be able to use my computer.



even more info:
I just found out there was a button on the side of my laptop to access boot options, so I can boot the Ubuntu installation process from my USB but I eventually get the (initramfs) error: "Unable to find a medium containing a live file system" after several usb errors:

```
usb 1-2: device descriptor read/64, error -110
usb 1-2: device descriptor read/64, error -71
usb 1-2: device descriptor read/64, error -71
usb 1-2: device descriptor read/64, error -71
usb 1-2: device not accepting address 4, error -71
usb 1-2: device not accepting address 5, error -71
usb usb1-port2: unable to enumerate USB device


BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system
```

---

### Post by erik37 on 2015-12-30
Bump. :(

---

### Post by Bucky Ball on 2015-12-30
Welcome. 

How did you create the USB installer? 
Did you run the option 'Check for defects' from the first screen with the options 'Try' 'Install' etc. when you booted the USB first time?
How did you partition the drive (as in what partitions did you create and size)?
Are you dual-booting with Windows?

---

### Post by erik37 on 2015-12-30
> **Bucky Ball said:**
> Welcome. 

How did you create the USB installer? 
Did you run the option 'Check for defects' from the first screen with the options 'Try' 'Install' etc. when you booted the USB first time?
How did you partition the drive (as in what partitions did you create and size)?
Are you dual-booting with Windows?

- I used UUI to install by USB: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

- I did not run the "check for defects" option before installing, but trying now gives me several USB errors (followed by an Ubuntu loading screen) and eventually "(initramfs) Unable to find a medium containing a live file system."

- I created the partitions following [https://youtu.be/0W7XYAB4cLc](https://youtu.be/0W7XYAB4cLc) (although my installation screen looked slightly different with buttons) and from what I remember, I had 500gb of space in sda5 where I added each partition that he made in the video to the END of the space I had, and used "logical" instead of "primary" when doing the type of partition. I also didn't have the option he had 9:05 into the video... my installation just skipped to the manual partitioning screen. I gave 16GB space for the ext4 partition and I believe 3GB for the swap partition, but I don't remember. I made it to the end of installation (15:50 into the video) and then the restart gave me the problems I now have.

- Yes. At least, I was... but now I have no option to boot from windows. :(

---

### Post by Bucky Ball on 2015-12-30
*Thread moved to **Installations and Upgrades**.*

My suggestion? Get the torrent file for the ISO [from here]("http://www.ubuntu.com/download/alternative-downloads") and torrent it down. Go for 14.04.3 under the heading 'Bit Torrent' a little down the page. That will be fault free when it gets to your end, but check anyway, and try again. Sounds like you have a dodgy ISO or a dodgy USB or both if you are getting errors when you check the device. Not a good sign in any case.

The partitions you need for a standard Ubuntu (not the flavours as some are more lightweight and don't need such a big / partition):

/ = 20-25Gb
/swap = 2Gb

This depends, of course, if you are intending to keep your personal data on a separate data partition which you may want to share with Windows (in which case, make that NTFS, but you can create that later if you like; might make things less confusing that way). When you're manually partitioning, just don't touch the existing Win partitions. 

Also, if you have Win installed and booting using UEFI, not BIOS mode, then you MUST install Ubuntu in UEFI. Also, before installing, you need to boot to Windows and switch off hibernation and faststart. Essential. Could be the cause of your problem here. Hard to tell just yet.

---

### Post by erik37 on 2015-12-30
> **Bucky Ball said:**
> *Thread moved to **Installations and Upgrades**.*

My suggestion? Get the torrent file for the ISO [from here]("http://www.ubuntu.com/download/alternative-downloads") and torrent it down. Go for 14.04.3 under the heading 'Bit Torrent' a little down the page. That will be fault free when it gets to your end, but check anyway, and try again. Sounds like you have a dodgy ISO or a dodgy USB or both if you are getting errors when you check the device. Not a good sign in any case.

The partitions you need for a standard Ubuntu (not the flavours as some are more lightweight and don't need such a big / partition):

/ = 20-25Gb
/swap = 2Gb

This depends, of course, if you are intending to keep your personal data on a separate data partition which you may want to share with Windows (in which case, make that NTFS, but you can create that later if you like; might make things less confusing that way). When you're manually partitioning, just don't touch the existing Win partitions. 

Also, if you have Win installed and booting using UEFI, not BIOS mode, then you MUST install Ubuntu in UEFI. Also, before installing, you need to boot to Windows and switch off hibernation and faststart. Essential. Could be the cause of your problem here. Hard to tell just yet.

The USB is brand new and worked fine on my computer before this happened. It still works on other computers in my family, and I will have to borrow one to torrent the ISO as soon as I can tomorrow. 

Two problems in partitioning are that I only allocated 16GB space, and I also don't recall calling the swap by "/swap" (it probably did it automatically) although I definitely set the ext4 partition as "/".

I also don't have the option to use Windows anymore when booting... Ubuntu is the only option besides USB.

Thanks for the help, I'll let you know how the new ISO goes.

---

### Post by Bucky Ball on 2015-12-30
You don't need to torrent the file to the install device. Not the way it's done. You download/torrent the ISO then create the USB installer with the software of your choice, Universal USB install, UNetbootin, whatever.

Just wipe the USB you already have, partition it as FAT32, then burn the image to it using one of the apps I've just mentioned.

---

### Post by erik37 on 2015-12-31
> **Bucky Ball said:**
> You don't need to torrent the file to the install device. Not the way it's done. You download/torrent the ISO then create the USB installer with the software of your choice, Universal USB install, UNetbootin, whatever.

Just wipe the USB you already have, partition it as FAT32, then burn the image to it using one of the apps I've just mentioned.

Re-downloading the ISO onto my USB allowed the USB boot to work. I then went through reinstalling Ubuntu *alongside* whatever else I had downloaded. Now when I select the newly-installed Ubuntu it will give me the following error: 

```
ACPI PCC probe failed.
Gave up waiting for root device. Common problems:
(etc.)
```

** Edit: I tried downloading a 3rd time, and cancelled the installation which took me to the Ubuntu desktop. I can do things now, but I'm not sure what will happen if I restart. :P

---

### Post by erik37 on 2015-12-31
Doing "sudo fdisk -l" now gives the following:

```
[FONT=arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]Disk /dev/sda: 500.1 GB, 500107862016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0x99d6776b[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1               1   976773167   488386583+  ee  GPT[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]

[FONT=arial]Disk /dev/sdb: 31.3 GB, 31306285056 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 3806 cylinders, total 61145088 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdb1   *          64    61145087    30572512    c  W95 FAT32 (LBA)[/FONT]
```

This is confusing me because I had 6 partitions (sda1, sda2, etc.) before Ubuntu... and I still can't find Windows. :(

---

### Post by ubfan1 on 2015-12-31
Try using gdisk -l , that will handle gpt disks.  A good thing to run before any restart would be sudo update-grub.

---

### Post by erik37 on 2015-12-31
> **ubfan1 said:**
> Try using gdisk -l , that will handle gpt disks.  A good thing to run before any restart would be sudo update-grub.

"gdisk -l" gives the following:

```
GPT fdisk (gdisk) version 0.8.8

Problem opening -l for reading! Error is 2.
The specified file does not exist!
```

"sudo update-grub" gives the following:

```
/usr/sbin/grub-probe: error: failed to get canonical path of '/cow'.
```

---

### Post by ubfan1 on 2015-12-31
try
sudo gdisk -l /dev/sda
and post the results.

---

### Post by Bucky Ball on 2015-12-31
As mentioned, you must switch off hibernation and faststart when booted in to Windows then shut down the computer completely (no standby or hibernate or restart) prior to installing Ubuntu. Did you do that?

Also mentioned, if Win is installed in UEFI mode (you can check in the BIOS) then Ubuntu must be installed in UEFI mode also. Is that the case? I have a feeling not. 

Perhaps use Boot Repair to give us your boot info. When you launch Boot Repair, you have two options. Click the one to 'Create bootinfo summary'. That will give you a link when it's done. Post that link here and we can have closer look at what you have going on here.

My guess is that Windows is not gone, just hiding, but we'll soon see. ;)

---

### Post by erik37 on 2016-01-01
> **Bucky Ball said:**
> As mentioned, you must switch off hibernation and faststart when booted in to Windows then shut down the computer completely (no standby or hibernate or restart) prior to installing Ubuntu. Did you do that?

Also mentioned, if Win is installed in UEFI mode (you can check in the BIOS) then Ubuntu must be installed in UEFI mode also. Is that the case? I have a feeling not. 

Perhaps use Boot Repair to give us your boot info. When you launch Boot Repair, you have two options. Click the one to 'Create bootinfo summary'. That will give you a link when it's done. Post that link here and we can have closer look at what you have going on here.

My guess is that Windows is not gone, just hiding, but we'll soon see. ;)

As mentioned, I have no access to Windows so there is no way for me to disable those options in Windows.

Windows was installed in UEFI mode, but is no longer listed. Ubuntu is listed instead.

& boot repair gives the following: paste.ubuntu.com/14354971 -- Of course I can tell from this that Windows is no longer on my PC but how do I get Windows back? x_x

---

### Post by Bucky Ball on 2016-01-01
How do you get it back? You reinstall it or you [use testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to attempt to retrieve the wiped partitions and put your disk back as it was. [SystemRescuCD]("http://www.sysresccd.org/SystemRescueCd_Homepage") has both testdisk and photorec included (the latter can retrieve files only if required). 

Then you boot to Win, switch off hibernation and faststart and install Ubuntu in UEFI mode, same as Win, not BIOS mode, and things should work.

If you need to reinstall Win, then you can install it in either UEFI or BIOS. The only thing to remember is that whatever you use, Ubuntu must be installed in the same mode and hibernation and faststart need to be OFF in Win. You need to be able to shut the computer down totally, no hibernation or suspend in Win, to install Ubuntu.  

Good luck.

---

### Post by erik37 on 2016-01-01
> **Bucky Ball said:**
> How do you get it back? You reinstall it or you [use testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to attempt to retrieve the wiped partitions and put your disk back as it was. [SystemRescuCD]("http://www.sysresccd.org/SystemRescueCd_Homepage") has both testdisk and photorec included (the latter can retrieve files only if required). 

Then you boot to Win, switch off hibernation and faststart and install Ubuntu in UEFI mode, same as Win, not BIOS mode, and things should work.

If you need to reinstall Win, then you can install it in either UEFI or BIOS. The only thing to remember is that whatever you use, Ubuntu must be installed in the same mode and hibernation and faststart need to be OFF in Win. You need to be able to shut the computer down totally, no hibernation or suspend in Win, to install Ubuntu.  

Good luck.

Thank you for those links! I will try tomorrow, and reinstalling the ISO on my USB like you said at least fixed Ubuntu's boot problems. I consider my problems solved. :)

---

### Post by Bucky Ball on 2016-01-01
> **erik37 said:**
> I consider my problems solved. :)

All good. Please see the first link in my signature (marking as solved will not close the thread), post a new thread if you hit any brickwalls, and good luck! :)

---

