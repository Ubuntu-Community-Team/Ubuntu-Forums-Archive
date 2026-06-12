---
title: "New Install Problems UEFI vs Std - not seeing Windows 7 install"
date: 2015-02-23
forum: Installation &amp; Upgrades
---

### Post by mike293 on 2015-02-23
Hello, I have been reading install articles and help for the last several hours and just cannot fix this issue.

I downloaded the latest Xubuntu and copied it to a bootable USB stick.  It works, looks great, so I tried to install it.

In my bootup, I use F12 to select boot options.  I selected UEFI USB drive to get to Xubuntu.  After testing it, I tried to install it both from within Xubuntu (icon on desktop) and from the "Try..." "Install" option upon boot.  When I boot with the UEFI USB option, the install does not see my existing Windows 7 OS.  I abort the install since I want to run a dual-boot setup and do NOT want to erase or tamper with my Win 7.

If I select the standard Flash drive option during boot up, I can test Xubuntu and at the installation screen, it sees Windows 7 and the option to install alongside of it, which is what I want.  However, after scanning the hardware, the install only shows an external USB drive as an option...yet I have other drives internal (SATA III) and even partitioned drives for Xubuntu prior to this to prepare it for installation.  /dev/sdb2 is an extended partition of 20 GB, with sdb5, sb6 & sdb7 formatted for Linux/Xubuntu

I have yet to use the many tools out there to modify my MBR since I'm not sure which one to use or how it's used (safely).

I ran Boot Repair.  Here is the link to the info it provided:

[http://paste.ubuntu.com/10374125/](http://paste.ubuntu.com/10374125/)

I used Linux (Red Hat and openSUSE) many years ago and it was primitive but these new builds are looking really good and I would like to install this, if possible.

Windows 7 is still booting and working.  I just want to install Xubuntu and dual-boot.

Thank you for any help you may provide.

Mike

---

### Post by oldfred on 2015-02-23
All your drives are MBR(msdos) which you can only boot in BIOS mode from.
UEFI requires gpt partitioned drives. And Windows only boots in UEFI mode from a gpt drive.

But since your Windows install is BIOS based, best to also install Ubuntu in BIOS mode. Unless you want to experiment with UEFI on a separate gpt partitioned drive, but then cannot dual boot from grub, only from UEFI menu or perhaps one time boot key.

Since you have multiple drives, you need to use Something Else install option. Do not use any auto install options.

Examples of Something Else installs:
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by mike293 on 2015-02-23
Thank you for the detailed reply, oldfred.

Is there no way to convert MBR to GPT without reformatting/erasing the Windows drives?  I thought UEFI was more efficient and current than the older MBR/Bios formatting?

When I boot the UEFI USB stick with Xubuntu, Xubuntu accesses "sees" all my drives but does not recognize Windows 7 as an existing OS.  If I boot to the USB stick without UEFI, Xubuntu only sees the one external USB drive.  

With that in mind, I need to boot the USB stick/Xubuntu in UEFI mode and use the Something Else type of install, correct?  If so, this will replace the MBR boot record and I won't be able to load Windows 7?

EDIT:  Never mind.  The more I read your links, the more I'm understanding this.  I'm ready to dive in to this.  I'll report back and close the topic if it is solved.  Thanks!

---

### Post by oldfred on 2015-02-23
I always suggest good backups before making any major change to system.

And UEFI suggests the efi partition should be first, although most Windows installs make it second or third but still near beginning of drive. Not sure if required or not. 
So usually better to partition from scratch with the efi partition first on drive.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

I typically partition in advance, but still have to use Something Else as I do not want just / & swap. And any install to second drive requires Something Else install.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

