---
title: "Windows 10 blocks during start-up after installation of Ubuntu 14.04"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by ManuTOO on 2015-11-23
Hello,

I have installed Ubuntu 14.04 on my old PC using ubuntu-14.04.3-desktop-i386.iso on a Thumb Drive (ie: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ).

Ubuntu is working nicely, but now when I select "Windows 7" in the boot menu (I guess it shows 7 because I upgraded from 7 to 10), then I can see Win10 starting up, having HD access for a few seconds, and then the HD activity stops, and it gets stuck forever on the black screen with the blue window & the rotating dots.

Windows self-diagnosis doesn't find anything wrong.

I found some topics with similar issues, but the solutions were all about EFI.

My Mobo is really old, it's an Asus Maximus Formula 1 (year: 2008) without EFI support.

Anyone would have any idea about what to do ?

I guess I could reinstall Win 10, but then I'm afraid I'd lose Ubuntu access.

Thanks in advance for any help ! :)


**EDIT:**
I just tried the default mode of Boot Repair ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ), but it didn't work any better...
=> [http://paste.ubuntu.com/13487189/](http://paste.ubuntu.com/13487189/)

---

### Post by ManuTOO on 2015-11-23
I just tried the default mode of Boot Repair ( [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ), but it didn't work any better...
=> [http://paste.ubuntu.com/13487189/](http://paste.ubuntu.com/13487189/)

---

### Post by grahammechanical on 2015-11-23
> grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
grub-install: warning: Sector 33 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.


Do you know what flexnet is?

And then there is this

> The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.mount -t ntfs-3g -o remove_hiberfile /dev/sda1 /mnt/boot-sav/sda1 The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount. Failed to mount '/dev/sda1': Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume read-only with the 'ro' mount option.

I guess that Windows 10 like Windows 8 shuts down by hibernating. And that might be causing some problems.

Regards.

---

### Post by oldfred on 2015-11-23
Flexnet is from Windows DRM software. Grub & Flexnet used to overwrite each other creating huge issues, but grub was modified to write around flexnet.         Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 

Windows 10 is just like Windows 8 whether UEFI or BIOS you must have fast start up off or its always on hibernation to be able to boot from grub.

You probably have to use Boot-Repair to install a Windows boot loader temporarily to MBR to boot into Windows and turn off fast start up. The restore grub. Make a Windows repair flash drive as grub only boots working Windows and Boot-Repair or Linux can only make very minor repairs to Windows.

      
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html
[/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
[/URL]

---

### Post by ManuTOO on 2015-11-24
@oldfred,
I restored the MBR with Boot-Repair, and now the boot loader is removed and it boots directly to Win10, but it still doesn't work better. I tried to repair stuff but I came into a strange "the drive where windows is installed is locked" message for which there's no easy solution, so I guess I'm good to reinstall Win7, hopefully it'll work better with Ubuntu. (and I'll be spared all the Win10 silliness ;) ).

Thanks for the head-ups anyway !

---

