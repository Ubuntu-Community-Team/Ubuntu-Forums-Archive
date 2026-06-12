---
title: "Can Ubuntu install and boot from external HD while still boot window off internal HD"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by mruschmann on 2010-10-23
Can Ubuntu install and boot from external HD while still booting windows off internal HD?

In an attempt to spread Ubuntu my friend wants to use ubuntu off an external HD and still have windows fully operational on the internal HD.  Questions:

1) Can Ubuntu install on external HD without tricky mounting methods and if so how do I go about it?

2) The bois have the capability to boot from usb, will grub work?

3) If the external is not plugged in will they be able to boot windows sufficently?

Thanks for help.

---

### Post by efflandt on 2010-10-24
Yes I am posting this from 64-bit 10.10 booted from USB hard drive (WD Passport).  I have not touched the internal drive of my new PC until I am sure that I have that system backed up.  I also do that for a work laptop, since it already has 4 partitions due to Dell Recovery and some media player app that can play media without running Windows, and since it is a work laptop, I don't want to tamper with it.

Some people recommend unplugging your internal drive when installing to USB, so you do not make a mistake.  That is not necessary if you are familiar with Linux drive /dev names and pay attention to how to put grub on the mbr of the USB drive (instead of default to your main hard drive).  But it is a good idea to unplug your internal drive if you are not really familiar with Linux and grub yet.

For Ubuntu 10.04 or earlier, after you select how to partition the drive and info for your username and password, at the summary screen just before it starts installing, the **Advanced** button selects where you want to put grub.  Not sure how the release version of 10.10 handles that, but in the beta version, when I used Advanced manual partitioning mode to select what partitions I wanted to use, when I put / in a USB drive, it automatically defaulted to putting grub on the USB mbr.

Booting will not be as fast as from an internal hard drive but is almost as fast as my old computer from 2004, and faster than all but expensive USB flash.  For example for sudo hdparm -t /dev/sd**a** (where **a** is different letter for other drives):

Old PC - 200 GB PATA internal /dev/sda:
 Timing buffered disk reads:  148 MB in  3.01 seconds =  49.11 MB/sec

Old PC - HP 4 GB usb flash /dev/sdf:
 Timing buffered disk reads:   66 MB in  3.06 seconds =  21.59 MB/sec

New PC - 1 TB SATA internal /dev/sda:
 Timing buffered disk reads:  352 MB in  3.00 seconds = 117.20 MB/sec

New PC - 500 GB WD Passport usb (boot drive) /dev/sdf:
 Timing buffered disk reads:   98 MB in  3.02 seconds =  32.47 MB/sec

New PC - same HP 4 GB usb flash /dev/sdg:
 Timing buffered disk reads:   66 MB in  3.03 seconds =  21.81 MB/sec

A usb stick or SDHC capable of 32 MB/sec would be more expensive per GB than a usb hard drive.

Sometimes you have to press a key (usually F12 or Esc) during BIOS splash screen to select boot device, even if you put USB first in boot order in CMOS setup.  If a system cannot boot USB, web search "boot from usb without bios support" for boot floppy or CD.

---

### Post by sikander3786 on 2010-10-24
Most questions have been answered in detail by **efflandt**. I would just like to add something.

> For Ubuntu 10.04 or earlier, after you select how to partition the drive and info for your username and password, at the summary screen just before it starts installing, the Advanced button selects where you want to put grub. Not sure how the release version of 10.10 handles that, but in the beta version, when I used Advanced manual partitioning mode to select what partitions I wanted to use, when I put / in a USB drive, it automatically defaulted to putting grub on the USB mbr.

In 10.10, you have the option to select the location of Grub from the drop down menu on the Manual Partitioning page just near the bottom.

However, I feel it safe to just disconnect the internal HDD and then install Ubuntu on the external one. That way you don't have to worry about messing up your HDD's MBR. Grub will get installed by default on the USB.

> Sometimes you have to press a key (usually F12 or Esc) during BIOS splash screen to select boot device, even if you put USB first in boot order in CMOS setup. If a system cannot boot USB, web search "boot from usb without bios support" for boot floppy or CD.

In addition to that, after you are finished installation, connect your internal HDD, boot into Ubuntu and run

```
sudo update-grub
```

It will pick Windows and add it to the Grub menu. Then you can select your USB as the first boot device, use Grub to boot both into Windows and Ubuntu. And if you disconnect it, you will automatically be booting off the internal HDD.

---

### Post by try2hard on 2010-11-03
I must be doing something wrong. 
I am trying this on my iMac Intel with 10.10 and it will not boot from my USB Hard Drive. I know the USB booting is tricky on Macs but I pluged it into my Lenovo PC also and set BIOS to boot from USB. The screen just sat black with a blinking cursor.

During install, I just selected to use entire drive and let it do its thing. What am I doing wrong? I rebooted from the Live CD, opened GParted and looked at the drive. 

It was in three partitions (which I allowed Ubuntu to do what it wanted to do):

Sdb1: 10MB Boot Partition

Sdb2: 200GB / root Partition (ext4)

Sdb3: 2GB /swap Partition

It also used a GUID partition table. Is that a problem? Should it be a MBR instead?

---

### Post by oldfred on 2010-11-04
try2hard

Your issue is a lot different both because it is a mac and  with gpt partitions. I have used gpt on an internal drive and grub needed a bios_grub partition for the grub files (but I have BIOS not EFI). If you using a mac you also may need an efi boot partition? I do not know macs, but there is an Apple sub forum and I would suggest you start a new thread there.

---

### Post by try2hard on 2010-11-04
I understand the Mac booting issue and EFI however, why would it not boot on my PC? Is it because Ubuntu choose a GUID partition table for the drive? It just sits with a blinking cursor. No GRUB menu, errors or anything. 10.10 is a stable version right?

---

### Post by oldfred on 2010-11-04
Grub does not present the menu if you only have one system. You have to hold down the shift key from BIOS until menu appears. The flashing underscore is standard after menu for a few seconds until logo appears. Your PC may then have the very common video issue which many seem to have. Many-many posts in this forum on various video cards/chips not working without additional parameters on boot line in grub menu.

---

### Post by srs5694 on 2010-11-04
I suspect GRUB issues. For starters, try downloading [Super GRUB 2 Disk](http://www.supergrubdisk.org) and use that for testing. This is a bootable CD that can detect GRUB installations and use the configuration files on your hard disk to boot even if GRUB isn't working correctly from the hard disk. You can boot the Super GRUB 2 Disk on your PC or (if you hold down the Command Key or Option key or whatever it is while booting) on your Mac. FYI, GRUB consists of several parts, including code in the MBR, code in the BIOS Boot Partition for BIOS-based systems, code in an EFI System Partition for EFI-based systems, code in the Linux root (/) or /boot partition, and configuration files in all sorts of places. I'm just pointing this out so you're aware of the confusingly scattered nature of GRUB.

Beyond this, GRUB on a BIOS-based system and GRUB on an EFI-based system are two very different things. Chances are your Mac installation created a BIOS-style setup, possibly under the assumption that you'll be dual-booting with a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) configuration, which IMHO is a bad idea if you can avoid it. It's unclear if either of your disks really is a hybrid MBR. If not, that could explain why your Mac-side installation isn't booting. To fix it, IMHO the way to go is to uninstall the grub-pc package and install the grub-efi-ia32 or grub-efi-amd64 package (whichever suits your Mac's architecture). You may also need to install rEFIt. I'm still experimenting with my somewhat elderly Mac Mini 1,1, but that combination seemed to work pretty well for me.

On the PC side, you'll need grub-pc (or some other boot loader, like LILO) installed in the MBR. Chances are your system was set up like this, but obviously something's wrong. Maybe you told it to install somewhere other than the MBR, or maybe your PC isn't set to boot from a USB device. You could try attaching the disk to the computer, booting the Ubuntu installer, and running the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) which scans your disks and produces a report with lots of data. Try posting that here, preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

---

### Post by forevermurphys on 2010-11-09
> **sikander3786 said:**
> Most questions have been answered in detail by **efflandt**. I would just like to add something.



In 10.10, you have the option to select the location of Grub from the drop down menu on the Manual Partitioning page just near the bottom.

However, I feel it safe to just disconnect the internal HDD and then install Ubuntu on the external one. That way you don't have to worry about messing up your HDD's MBR. Grub will get installed by default on the USB.



In addition to that, after you are finished installation, connect your internal HDD, boot into Ubuntu and run

```
sudo update-grub
```It will pick Windows and add it to the Grub menu. Then you can select your USB as the first boot device, use Grub to boot both into Windows and Ubuntu. And if you disconnect it, you will automatically be booting off the internal HDD.



Is this what I need to do then? I installed 10.10 on an external USB drive and now XP won't boot unless the USB drive is plugged in.

---

### Post by oldfred on 2010-11-09
forevermurphys - you installed grub to the MBR of the internal drive. You need to install grub to the external's MBR and reinstall a windows boot loader to the internal's MBR. These instructions cover both from your Ubuntu install. You can also restore windows boot loader with windows repair CD and the grub while booted or from a liveCd.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by forevermurphys on 2010-11-09
Thank you that worked perfectly. :mrgreen:

---

