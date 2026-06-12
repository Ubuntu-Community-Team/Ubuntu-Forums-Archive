---
title: "UEFI and additional partitions"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-10-07
As I understand it, UEFI (which I have on my machine) enables you to have more than four primary partitions.  Are there any Ubuntu partitioning tools that enable one to take advantage of that?  gparted doesn't seem to be able to do it.

---

### Post by darkod on 2012-10-07
No, UEFI has nothing to do with the number of partitions, as far as I know.

It's the partition table type on the disk that controls that. The older type MBR (or MSDOS) table has the limitation of 4 primary partitions, or 3 primary and 1 extended holding more logical partitions.

The GPT table allows many partitions, there is no difference between primary and logical.

Windows 7 can use UEFI only with gpt table so someone might think the option to have more than 4 partitions is because UEFI, when in reality it's because of gpt.

Ubuntu does support gpt long time ago and you can have your disk with gpt table. But if you dual boot on the same disk, you have to use UEFI and win7 because of the mentioned limitation that it needs the combination of gpt+uefi to work.

---

### Post by coffeecat on 2012-10-07
> **pwabrahams said:**
>  gparted doesn't seem to be able to do it.

darkod has clarified the difference between UEFI and GPT. Gparted can both create a GUID partition table (GPT) and can create more than 4 partitions in a GPT drive.

---

### Post by pwabrahams on 2012-10-07
Well, right now my system is dual-booting into Windows 7 and Kubuntu 12.04.  It has MBR-type partitioning,and the BIOS tells me that it's UEFI-capable. Is there a way to convert it from MBR to GPT?  Or do I have to throw everything out (or copy it all to an external drive) and start over?

I suppose that if I do manage to do the conversion, I then have to figure out how to inform Windows 7 and Kubuntu where everything is, since the partition IDs will probably change.

I wish I had known about all this when I still had a factory-fresh machine.

---

### Post by darkod on 2012-10-07
I don't think you can convert it. You need to make a full backup of all your personal data from both OSs, and do clean installs.

Before starting the install, make sure you change to UEFI mode in bios, and to make a gpt table on the disk. Then install win7.

When installing ubuntu, make sure to boot the cd in UEFI mode (there will be an option for that in boot devices) so that it installs in UEFI mode. If you don't do that, the dual boot won't work.

---

### Post by pwabrahams on 2012-10-07
Switching to gpt sounds like a hopeless task, because I have no way of reinstalling Windows 7.  I'm afraid that if I tinker with it at all, it will fail the genuineness tests.

If anyone comes up with a way of converting a system with Windows 7 preinstalled (like most computers sold these days) to gpt with Linux in one partition, I'd love to hear about it.

---

### Post by oldfred on 2012-10-08
I have not idea if this works or not. First you have to have some space between MBR sectors for gdisk to let you convert from MBR to GPT. And you have to create the extra efi partition at the beginning of the drive and the Windows MSR near the start of the drive. Usually moving partitions around to allow for all that is not easy. And I do not know for sure where the Windows efi boot files are to copy, should be somewhere on a Windows install DVD set, but most Windows are pre-installed and will not have those files.

Of course full backups are absolutely required before even attempting something like this.

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](https://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

---

### Post by pwabrahams on 2012-10-08
The fact that I have Windows 7 preinstalled makes disruptions risky.  For instance, I could move the boot partition (sda1) with gparted, but that might cause the machine not to boot, or at least not to boot into Win7.  Those Microsoft articles seem oriented towards the case where you're starting with an empty disk.

---

### Post by bra|10n on 2012-10-08
I strongly advise against moving any existing partitions.

---

### Post by pwabrahams on 2012-10-09
The machine came with four primary partitions -- a difficult situation for installing Linux.  I ended up preserving #1 and #4, with #2 still a Windows primary and #3 an extended partition that in turn contained the original #3 (as a logical) and 3 logicals for Kubuntu.  And that has seemed to work.  But if Lenovo had taken full advantage of UEFI, things would have been easier and cleaner.

I figured I should leave #1 and #4 alone since #1 is the boot partition and #4 is the recovery partition.  Of course, there's now no way I can recover Windows without going back to the factory configuration, and even that might not possible any more.  So preserving #4 might actually be pointless.

---

### Post by oldfred on 2012-10-09
I have to agree that moving Windows partitions will cause issues. Most times but not always repairable. Windows has in its PBR - partition boot sector the start sector and size of the NTFS partition which then has to match the partition table. When you move a partition that data does not match. Often chkdsk will fix it, but...

Not sure if Lenovo does it the same way, but many Vendors let you boot into the Vendor recovery and make a set of DVDs. That should let you do that as hard drives eventually fail and you need a way to recover.

Better just to make a full backup of the entire Windows partition.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by pwabrahams on 2012-10-09
With hundreds of gigabytes of data floating around, much of it (like media files) not worth the effort of backing up, my strategy has been to keep the stuff I really don't want to lose at Dropbox.  For instance, I've created some symlinks so that my email (I use kmail) is kept at Dropbox.

I've made a set of recovery DVDs for Win7 with the factory configuration (one of the options that Win7 offers).  My first concern is that in the event of a crash, I don't want to lose the ability to have a validated copy of Win7.  Having all my other Linux stuff is also important, but not as much.  I've gone to a lot of work to collect the packages that I need in my system, and of course there's also the configuration data.  Not all of that is at Dropbox.

It may well be that at this point the recovery partition (#4) is useless because I've made so many modifications to the configuration, and restoring whatever it is that the recovery restores would destroy them all.  Still, I'm keeping it around just in case.

---

