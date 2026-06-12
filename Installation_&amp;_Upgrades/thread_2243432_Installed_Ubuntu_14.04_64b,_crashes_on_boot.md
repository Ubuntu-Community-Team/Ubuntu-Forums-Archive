---
title: "Installed Ubuntu 14.04 64b, crashes on boot"
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by Kevin_Nauta on 2014-09-08
Hello,

I recently built a new pc, and put windows 7 Professional N on it (64b).

Now I wanted to make a dualboot install with Ubuntu 14.04, and downloaded the appropriate iso as such, made a liveboot usb stick something with it, and installed.
I had some friends help me who had sufficient experience in the field, and I was confident that it would work.

I have a 256 GB SSD, and a 1TB HDD. (other specs below)
Windows had approx. 70GB taken on the SSD, and i had some files stored on the HDD for ~8GB.
I made an 8GB swap partition on the HDD, and a 35GB parition for Ext4 to install ubuntu on.

Then I installed the bootloader on the HDD, so that I can choose to boot to either when booting from HDD, or boot directly to windows if booting from SSD (and because if I installed it on the SSD, I would lose my entire Windows OS, as I was told).

Now, time and keyboard probably aren't that important, and when I had installed the entire OS and got a message that I had to reboot, I did so.
First time, I left the USB stick in, and I got to see some sort of GRUB menu (worked with it before, and looked reasonably like it, though nowhere was Windows to be seen) which had the following options:

> Ubuntu
> Advanced options for Ubuntu
> System setup

The second would show four versions of ubuntu with versionnumbers next to it, of which two were recommended or something.
The third would error: couldn't find command 'fwsetup'
The first would stop showing up on the screen (check cable connection, an error from the display itself), and I would hear the drumsound once, then a short break (half a second), then the drumsound infinitely repeating.
Restarted, booted to windows, it wanted to do a consistency check for both disks, but everything seemed fine.

And everything *was* fine, except for the system time which was set back 2 hours, but oh well :P

So I formatted the usb stick again, put ubuntu on it again (this time with PenDriveLinux on Windows OS, previous one was on Ubuntu 12.04 on my laptop with a built-in program) and tried again.
Same settings, same everything. 
One thing to note: when installing I was asked if I wanted to install Ubuntu besides Ubuntu (the previous install), install it instead of Ubuntu, or choose other settings (which I did, to make sure the partitions were allright).

Same result. Nothing on the displays, drumsound once, pause, drumsound infinitely repeating.
Windows didn't perform any consistency checks or whatever, and booted normally, though again the time was set back 2 hours.

Tried rebooting, but never again was I shown the 3 options menu as put above, not even after the first install, after trying to boot ubuntu again.


Does anyone have any ideas to what caused it, why it happened to me twice, and how to fix this (prefferably in that order, so I can learn from it)?

Thanks in advance!

PC Specs:
 - 256 GB Crucial SSD
 - 1 TB WD HDD
 - Samsung CD station thingy
 - 8 GB ram (2x4GB)
 - Intel i5 4690 & Mugen 4
 - Sapphire Radeon R9 290 Tri-X w/ 4GB memory
 - Dual BENQ 22" monitors setup
All put together nicely in a CM 690 III window Case

Usb: Kingston DataTraveler G4 w/ 8GB
Newly bought to install Windows on the pc, only used a couple of times afterwards to copy files from laptop to desktop.

---

### Post by yancek on 2014-09-08
Probably the best next step is to download and run the bootinfoscript to gather pertinent information.  Get it at the link below.  You need to run it from Linux so if you cannot boot the installed Ubuntu, do it from the installation medium for Ubuntu.  Instructions are in a link in the Description box at the site:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by fantab on 2014-09-09
Boot with '[nomodset]("http://ubuntuforums.org/showthread.php?t=1613132")' kernel option, which will temporarily disable your GPU and load Ubuntu in failsafe graphics mode.
How did you set up your Windows? that is, is it a UEfI install or did you install it in 'legacy' mode'?
Also post the output of:
```
sudo parted -l
```

---

### Post by Kevin_Nauta on 2014-09-09
Back again.


Yancek: BootInfoScript provided this file:
[ATTACH=CONFIG]256308[/ATTACH] ( [.spoiler][./spoiler] doesn't seem to work, sadly)


Fantab: The 'Parted -l' results:
[spoiler]Model: ATA Crucial_CT256MX1 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system  Flags
 1      1049kB  106MB  105MB   primary   ntfs         boot
 2      106MB   221GB  221GB   primary   ntfs
 3      221GB   256GB  35.0GB  extended
 5      221GB   256GB  35.0GB  logical   ext4




Model: ATA WDC WD10EZEX-08M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ntfs            boot
 2      992GB   1000GB  8000MB  extended
 5      992GB   1000GB  8000MB  logical   linux-swap(v1)




Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 7867MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  7860MB  7860MB  primary  fat32        boot, lba
[/spoiler]
[ATTACH=CONFIG]256309[/ATTACH]


I installed Windows with UEFI mode.
Booting with 'nomodeset' (as opposed to 'nomodset' which you typed, probably a typo because the link showed 'nomodeset' and so I went with that one) didn't really get me any further, sadly.
I was able to get to the GRUB menu by holding shift while booting, as told at the link you provided, took the newest (3.13.0-35 generic) of the 'advanced options for ubuntu' tab, and added the kernel command.


Then Ctrl+X booted it, and I saw some sort of checkerboard of purple and darker purples, and the upper line of ~10 pixels showed icons with a bar trough them roughly at pixel 8.
The bottom lines of these things also overlapped with the 'booting a command line'. Underneath was a newline, and 'Loading linux 3.13.0-35 generic...' Underneath that was the cursor, or at least an underscore which didn't blink at all.
See picture for checkerboard: [IMG]https://www.dropbox.com/s/5oa1kd2kqgcu1g5/2014-09-09%2022.54.59.jpg?dl=0[/IMG]


After a couple of minutes, it still hadn't done anything, and the screen went black (sleep mode I guess, after moving the mouse it woke up again).
I had decided that it, again, had frozen completely, and rebooted back to windows...

Any ideas now?

---

### Post by fantab on 2014-09-10
> ============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 112 for .

In your BIOS menu set your second HDD or the on which Ubuntu is installed as your 'first boot device'...

---

### Post by Kevin_Nauta on 2014-09-10
Fantab,

Do you mean the actual OS, or the bootloader?

I installed the OS on the SSD, but the bootloader on the HDD.
If I were to set the SSD as first, then I simply boot to windows, so I'm thinking you mean the bootloader, and therefore the HDD as first booter.

Problem is: I've already tried that, with the results from above: drumsounds and no displays.
If i set the boot priority to the SSD, then I can normally use windows.

Not sure where you're trying to get to here... :S

---

### Post by oldfred on 2014-09-10
It is ok to have grub in sdb with install on sda, just not normal. I currently boot sdc for install on my sdd SSD.

But you seem to be past boot issues as if you get drum sound it is booting. 
Since it did not initially find Windows it thinks it is the only install so does not normally show grub menu. Shift key from BIOS should then show menu.

Have you tried recovery mode or second entry in grub menu. That has nomodeset as default entry.

You need to get proprietary video driver installed.
       AMD Radeon R9 290 On Ubuntu 14.04 With Catalyst Can Beat Windows 8.1
 the open-source AMD Hawaii support remains broken,
[http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1](http://www.phoronix.com/scan.php?page=article&item=catalyst144_win81_ubuntu14&num=1)
[http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_r9hawaii_linwin&num=1)

      
 open (Gallium3D) and closed-source (Catalyst) driver
      
 [URL="https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection"]https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection
[/URL]
 Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

[URL="https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection"]
[/URL]

---

### Post by fantab on 2014-09-11
> Problem is: I've already tried that, with the results from above: drumsounds and no displays.
If i set the boot priority to the SSD, then I can normally use windows

If you hear 'drumsounds' then you have installed ubuntu correctly and it is booting.
The issue appears to be with your Graphics.
Have your tried 'nomodeset' option when booting from HDD?

---

