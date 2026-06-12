---
title: "Yet another U/Win on separate disks question"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by dreamer371 on 2012-05-14
Setup:

* A new two disk HP box which is Ubuntu certified hardware.
* Windows 7 on one disk and the other is empty.
* Official HP recovery disks (didn't make them myself with the HP utility).
* Official Ubuntu V11.10 installation DVD.
 

Problem:

Install Ubuntu on the empty disk without modifying the Windows disk in any way and without disconnecting the Windows disk (computer supplier may object, can't easily identify which disk to disconnect, disk connectors are designed for minimal manipulation).
 

Prefered Solution:

Have only the Windows boot loader on the Windows disk and only GRUB on the Ubuntu disk. I'll set the BIOS boot order so the OS used more frequently is first to boot. The other OS will be booted via the startup boot menu which is easy to invoke.

 
Tech questions:

* If during installation the Ubuntu disk comes before the Windows disk in the BIOS boot order will the Ubuntu installer install its boot loader on the Windows disk?

* If during installation the Windows disk is disabled in the BIOS will the Ubuntu installer be able to access it directly, i.e. not via the BIOS?

* The official website recommended 32-bit Ubuntu and that's probably what I bought. Does it mean Ubuntu wouldn't be able to use RAM above the 4GB mark? Be slower?

 
Thanks a lot!

---

### Post by kc1di on 2012-05-14
Well in answer to your question #3 Ubuntu 32 bit comes with the PAE kernel so it can access more than 4 gigs of ram. 

I think your other question will depend upon the bios in that particular machine.  But you should be able to install grub in the root partition of the Ubuntu disk and not touch the window MBR. 
How ever you may still need a third party boot loader to point to it.  I don't see the need Grub works really well in booting windows and if it were me I'd just allow it to be the boot manager. 

Cheers!

---

### Post by dreamer371 on 2012-05-14
> **kc1di said:**
> Well in answer to your question #3 Ubuntu 32 bit comes with the PAE kernel so it can access more than 4 gigs of ram. 
 
I think your other question will depend upon the bios in that particular machine. But you should be able to install grub in the root partition of the Ubuntu disk and not touch the window MBR. 
How ever you may still need a third party boot loader to point to it. I don't see the need Grub works really well in booting windows and if it were me I'd just allow it to be the boot manager. 
 
Cheers!
 
Dave, thanks!
 
I'm a Linux programmer who uses Windows only for compatability with other users or when patent issues are involved so hearing that my Ubuntu will be able to use all RAM is good news.
 
A silly question: will the Ubuntu installer ask me where to put its boot loader code or will it install it without asking? If it lets me decide there is no problem.
 
I know that GRUB can boot Windows but I hear that sometimes there are problems when Windows finds its MBR was modified. Since I'm willing to occasionally use the startup boot menu I wouldn't need one boot loader to point to the other.

---

### Post by kc1di on 2012-05-14
I've never experienced any problems booting windows from grub
but that being said you should read through the install wiki.
It has the parameters you need.

[https://help.ubuntu.com/12.04/installation-guide/i386/index.html]("https://help.ubuntu.com/12.04/installation-guide/i386/index.html")

---

### Post by YannBuntu on 2012-05-14
> **dreamer371 said:**
> A silly question: will the Ubuntu installer ask me where to put its boot loader code or will it install it without asking? If it lets me decide there is no problem.


Your questions are not silly.
Ubuntu installer proposes different installation modes: automatic ones ("Install Ubuntu on the entire disk", "Install Ubuntu next to Windows",... which install GRUB in the first disk without asking ) , and advanced ones (which allows you to select where to install GRUB).

If you can disconnect your Windows disk during Ubuntu installation, i recommend you do it. Then you will be able to update GRUB to a add Windows entry in it.

If you can't, use the advanced partitionning and be careful not to erase the Windows boot partition (which is sometimes separate from the system).

---

### Post by oldfred on 2012-05-14
Another question as new systems may be UEFI or BIOS or have UEFI but still boot in BIOS mode.

If BIOS these links give examples of installs to second drives and you have to use the combo box to choose sdb as the location to install the grub2 boot loader. Assumes second drive is sdb. Sometimes if using USB flash to install, BIOS promotes flash to sda and renumbers all the other dirves. But combo box is by drive name not device sdb.

difference in install versions is not significant, Desktop (gui) can be lot different once installed. Manual install is now Something Else in newer versions.
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by dreamer371 on 2012-05-14
Thanks you all for the info and links!
 
Some tentative answers to my questions seem to be:
 
* The Ubuntu Desktop (graphical installation) DVD lets one decide where to install the boot loader so if you are carefull there is no need to physically disconnect the Windows disk in order to protect it. In order to get this option one should choose "Specify partitions manually (advanced)" instead of "Install alongside other operating systems" or "Erase and use the entire disk".
 
It may be a good idea to backup the Windows MBR to a USB stick before installation using the "dd" command from the Ubuntu live CD. The Windows MBR could probably be restored also with the HP recovery disks.
 
* The Ubuntu installer is said to install GRUB to the first disk's MBR by default. The Linux disk order is random, at least with SATA disks, unless ids/labels/paths/uuids are used. Changing the BIOS boot order before installation may change the Linux disk order if they are not used.
 
In short, changing the BIOS boot order would probably not change where the Ubuntu installer installs GRUB by default.
 
* Disabling the Windows disk in the BIOS may protect it if the Ubuntu installer uses BIOS calls and not direct hardware access. It's reasonable to suppose disabling protects.
 
* Using a 32-bit Ubuntu may be a reasonable choice, at least for a first installation.
 
Am I right?

---

### Post by oldfred on 2012-05-15
You should make a Windows repairCD. I do not like using dd as it is dangerous, if you do not use it precisely. MBR can easily be reinstalled unless you have a customized MBR and then a standard Windows type boot loader still usually works.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

My SATA drives are always port order, but USB flash drives sometimes are inserted in random order? Also When I specify boot drive as something other than sda, that drive is hd0 in grub, so sda is then hd1. Or drive numbers may change in grub2. More an issue if manually booting or chain loading with manual commands.

I would use 64 bit unless you have less than 3GB of RAM or use a very few vendor apps that do not like 64 bit.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

Manual install or now Something Else is the only way that you get to choose which drive's MBR you install the grub2 boot loader into. You then do have to manually specify / (root) and swap partitions and optionally /home (recommended).

---

### Post by dreamer371 on 2012-05-21
Thanks for all the info!
 
A nice installation guide:
 
  [http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/](http://www.techspot.com/community/topics/step-by-step-beginners-guide-to-installing-ubuntu-11-10.172128/)

---

