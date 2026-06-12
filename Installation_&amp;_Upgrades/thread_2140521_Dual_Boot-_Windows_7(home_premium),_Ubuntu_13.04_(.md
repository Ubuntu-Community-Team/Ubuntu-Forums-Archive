---
title: "Dual Boot- Windows 7(home premium), Ubuntu 13.04 (ssd+hdd, uefi, gpt)"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by HappyFishFace on 2013-04-30
Hello. Recently I've been searching for a specific guide. One that would explain, in no uncertain terms, how to dual boot Windows 7 and Ubuntu on the same 120gb ssd, with a new uefi motherboard(asrock extreme4 z77). Needless to say, I've never quite found what i'm looking for. Does anybody know where such a guide exists, and can provide me with a link? Or if i have been efficient in my searching, and no such guide exists, could provide one.

Here are (hopefully) all the relevant system specs:
(going to be building it myself)
-i5 3570k
-asrock extreme4 z77
-8gb (2x4) ram (might upgrade to 16gb)
-gtx 660/760 (might sli)
-1 x 120gb ssd
-1 x 1TB hdd
-standard dvd burner/reader
(have access to a 16gb/32gb flash drive [based on need])

Any part is subject to change based on necessity or (reasonable) advantages 

I would like:
Both OS's on the ssd
Data on hdd
No constant problems resulting from this

Answers Requested:
-Link to guide(usable or spot on)
-Guide
-General Advice
-Partitioning help for hdd
-Anything at all useful
-Good times to do things like partition beforehand, or to try to move My Docs, or to make backups
-If you can explain complicated terms that you use, go for it!

Questions Answered:
I do not want to use wubi or a VM
I have decided completely on Ubuntu
Baring any specific failings, i would like to use these parts
I plan on using Ubuntu as a primary OS
I do game
All installs are completely clean, no data on hdd, non torrented Windows
I plan on having about 75gb for windows, and 45gb for Ubuntu(sound good?[running a VM of slackware on Ubuntu])
No, i have never used Ubuntu before. (Family computer- wouldn't be good to change OS on it)

Thanks in Advance(presumptuous, I know)

---

### Post by oldfred on 2013-04-30
If you have not run Ubuntu understand that Linux is not Windows. I was a CP/M, DOS, Novell, Windows 3.1, NT, 98, & XP users and it took me quite a while to feel confortable with Ubuntu. I really like a lot of things, but some are not the easiest to deal with.

The new UEFI has made everything more complex. If you do not have the pre-installed Windows 8 with secure boot then it is easier, but still will require some learning. 

We mainly use command line because there are many DE -Desktop enviroments and to try to walk thru using a mouse and clicking is difficult.

       Two Drive UEFI installs
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)

Do you understand partitioning and the difference between MBR(msdos) and gpt(GUID)? That is important as UEFI has to have the new gpt partitioning.

More technical info:

 [https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

      
 You will need to use the 64 bit version of 13.04, 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive. Reboot after shrink so it can run its repairs to its new size.
Backup efi partition and Windows partition before Install of Ubuntu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

If you have nVidia, you will need to learn to add nomodeset to linux boot line in grub menu. 
If not using BIOS skip the first part and look at installed screen. With UEFI installer you also get a similar grub boot loader screen and have to replace quiet splash with nomodeset.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by fantab on 2013-04-30
HappyFishFace, oldfred has covered in detail almost everything you need to know. I am just adding a few more links that have helped me and hope that you will find 'em useful too.

[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm").
[General Intro to Ubuntu]("http://www.psychocats.net/ubuntu/index").
[Understanding RootSudo]("https://help.ubuntu.com/community/RootSudo").

General Links to UEFI:
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
[http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](http://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)

[GPT vs MBR]("http://www.petri.co.il/gpt-vs-mbr-based-disks.htm")

You don't really need a guide for SSD, after all its just anoter kind of disk. So any partitioning guide for linux will do. Just one thing, from Mobo Bios setup change the SATA mode to AHCI, if its not already set to it by default. Try not to use RAID.
Your plan of 75:45 sounds good. However I would suggest another partition on SSD of about 20GB to install another version/flavor of Ubuntu or another Linux Distro. This is just planning ahead so if you in future need to install another Linux it will be useful.
Ubuntu "/" (root) partition won't need more than 30GB. "/" holds your system files like c: in windows.

EDIT: Note: Ubuntu can read and write to NTFS partition using ntfs3g driver but Windows won't work on Linux filesystems like ext2, ext3, ext4 or LVM etc. So if you want to share data between Ubuntu and Windows then having a common NTFS partition is suggested. However, NTFS is lousy filesystem to have, IMO. You can instead use a small NTFS partition on your HDD to share DATA and use the rest of the HDD for Linux DATA. 

Suggested Partition layout:
SSD:
70GB Windows Primary
30GB Ubuntu Primary
20GB Free Primary

HDD:
100-200GB NTFS shared between Windows and Ubuntu, Primary
800-900 Ext4 Linux partition, Primary


Since you are building your own system and want Ubuntu as a primary OS you might find [Ubuntu Hardware Support]("https://wiki.ubuntu.com/HardwareSupport") useful.

Good Luck...

---

### Post by oldfred on 2013-04-30
I also believe on a system on every drive, so I would allocated an efi partition and another 20  or 30GB for / on the hard drive even if you do not do that initially.

With UEFI the first partition in gpt partitioning must be a 200 to 300MB efi partition formatted FAT32, with Boot flag if using gparted to make it the efi. I would have that on both drives, since it is small even if booting from one drive.

---

### Post by HappyFishFace on 2013-05-09
Thanks for the help. I feel pretty confident now, ready to go past the limits of the windows operating system. Thanks again!

---

