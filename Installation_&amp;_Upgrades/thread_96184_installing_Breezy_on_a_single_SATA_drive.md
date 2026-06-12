---
title: "installing Breezy on a single SATA drive"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by Coogan on 2005-11-28
I recently bought a small system to use as a home server, and decided to go with a single SATA HD.  I put the system together and booted up Hoary on it, and when it got to the partition manager it said I didn't have any partionable media installed.  I tried several different things and couldn't get Hoary to see the drive.  I finally decided to download Breezy and give that a try.  While Breezy was downloading I pulled out an old 4.10 Live CD I had and booted that up.  Lo and behold, it saw the drive (/dev/sda1) but when trying to view the drive, it told me that it was not a valid block device.

Finally, I gave up trying and went out and bought a 120 gig IDE drive and put that in the system, and got Breezy installed (which still didn't see the SATA drive).

I spend most of Saturday night and Sunday morning searching these forums as well as Googling, but the only substantial information I can find all relates to installing a RAID on the system, which I do not want or need.  Does anybody know what I need to do to get this SATA drive recognized by the system?  The system is a Biostar iDEQ 210, which I believe has a Via chipset on it.

---

### Post by Coogan on 2005-11-29
Hello?

I'm guessing by the lack of replies that it is currently impossible to get a non-RAID SATA hard drive working in Ubuntu.

---

### Post by kalos on 2005-11-30
I'm not really sure if I understand this right, but I believe you can run RAID on just one drive (yes it's not redundant...). I have my data striped across one SATA drive, I believe it is in RAID 0 (which isn't redundant anyway). If you set up your SATA drive like that (you should be able to get into a utility on boot). Just be careful you don't lose any data. : )

I don't really know the particulars of the nForce3 chipset (I'm running a Promise FastTrack 376 controller and it is detected automatically). But try this [nVidia entry](http://linuxmafia.com/faq/Hardware/sata.html#nvidia) on linuxmafia listing of sata devices. It includes a link to the [nVidia binary driver](http://www.nvidia.com/object/linux_nforce_1.0-0310.html).

If you have Breezy running from your IDE drive, it might be easier to get the SATA recognized than to install onto the SATA.

---

### Post by incompetence on 2005-11-30
It seem not possible to install Breezy directly onto an SATA drive at the moment.
The driver needed for the SATA drive is not inside your Kernel. It is probably a module which needs to be loaded to be able to see the SATA drive.
It is of course possible to operate breezey on an single SATA drive. To do so, you need three things.
1. Install breezy onto an PATA drive and locate the module needed to get your SATA operational.
2. Install the kernel sorces and compile a new kernel with the needed module compiled into it. Make the kernel functional (grub etc)
3. Copy the whole system to the SATA drive. Use a live cd and chroot to make the SATA drive bootable.
This is of course too complicated for an newbie. All informations is available through google.

---

### Post by frodon on 2005-11-30
[QUOTE=Coogan]While Breezy was downloading I pulled out an old 4.10 Live CD I had and booted that up.  Lo and behold, it saw the drive (/dev/sda1) but when trying to view the drive, it told me that it was not a valid block device.
t.[/QUOTE]If you never used this disk before, it should not be formated so you can't use it and i think it's why you got these error messages, if you can't find a way in DOS to format the drive i advice you to plug your disk on another computer and then format it. It might solve your problem, i say that because i met some persons in this forum who never got any problems with SATA drives.

---

### Post by teaker1s on 2005-11-30
if live cd saw drive then you need to look at the usb ubuntu install on forum follow the part that tells you to edit grub list and edit yours with the /dev/sda1
if you still have no joy look at raid or fakeraid in wilki

---

### Post by YtiDilav on 2005-12-01
[QUOTE=incompetence]It seem not possible to install Breezy directly onto an SATA drive at the moment.
The driver needed for the SATA drive is not inside your Kernel. It is probably a module which needs to be loaded to be able to see the SATA drive.
It is of course possible to operate breezey on an single SATA drive. To do so, you need three things.
1. Install breezy onto an PATA drive and locate the module needed to get your SATA operational.
2. Install the kernel sorces and compile a new kernel with the needed module compiled into it. Make the kernel functional (grub etc)
3. Copy the whole system to the SATA drive. Use a live cd and chroot to make the SATA drive bootable.
This is of course too complicated for an newbie. All informations is available through google.[/QUOTE]

Ok, that's my problem i guess.

I am installing various distributions of Linux so i can verify that our products support those versions.  I was intending to have the supported list be: Red Hat, Fedora, Debian, Ubuntu, and CentOS.  But, i can't create partitions for Ubuntu with your installer.

I have a Dell Optiplex GX280, which has an SATA drive.  I installed Red Hat EL 3, then Red Hat EL 4.  I had no trouble installing the two RedHat's and fixing the grub.conf to boot either OS.  I was hoping to add Ubuntu, but i can't add partitions with the Ubuntu installer.

When i select "Manually edit partition table", i get the following options:
>     Configure software RAID
    Configure the Logical Volume Manager
    Guided partitioning
    Help on paritioning
    [two blank lines]
    Undo changes to partitions
    Finish paritioning and write changes to disk

By googling around, i see that my current hard drive is supposed to show up in that list between Help and Undo.  However, i have two blank lines where the hard disk selection should be.  I suppose it is because the support for SATA is not in the kernel of the Ubuntu installer.

Oh well, perhaps i will wait until the next version of Ubuntu.

---

### Post by kalos on 2005-12-05
[QUOTE=incompetence]It seem not possible to install Breezy directly onto an SATA drive at the moment.[/QUOTE]

Not quite true, since I have done so myself (using a different *SATA controller*. But for YtiDilav's purposes, yes, you cannot simply install. YtiDilav, you could either follow incompetence's steps, get a Linux compatible PCI SATA controller card, or wait for Ubuntu 6.04 - Dapper Drake.

-kalos

---

### Post by metoo on 2005-12-06
I would guess, that it has something to do with your chip set/BIOS setting.
I installed amd64 from an early installer CD in September on a System with 2 SATA only HDs non RAID. This was a VIA chip set K800Pro/ xx37 south bridge?

I had to set something in the BIOS, that it would use the SATA first and no RAID on it.

So check your BIOS.

Dell uses Intel CPUs, chip sets too? If it is the latest chip set, you might be out of luck here. Breezy uses still a 2.6.12 kernel after all.

Biostar is not so widely used. Check, whether you have the latest BIOS installed or upgrade the BIOS if a new version is available. Linux support for these small factor PCs is often not that good right from the vendor.

So it is possible to set up a system with a single SATA hd, but it depends on the BIOS and the chip set (and the kernel version).

---

### Post by linuxlady2714 on 2005-12-12
I'm trying as well to install Breezy on a new Dell Optiplex GX620 with a SATA drive.  I get the two blank lines between Help on partitioning and Undo changes to partitions. 

This is what I've tried so far: I updated the BIOS to the latest version, A05.  In the BIOS I changed the SATA setting from standard to combination.  It still does not work.

Has anyone got this to work?

:confused: 

linuxlady2714

---

