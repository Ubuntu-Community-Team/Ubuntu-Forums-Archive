---
title: "Remove Ubuntu and keep windows 10 Then install a fresh Ubuntu"
date: 2020-03-22
forum: Installation &amp; Upgrades
---

### Post by wildmanne39 on 2020-03-22
I have issues with not being able to update my bios/UEFI and I keep getting an error where my laptop tries to install a new bios update on its own but it fails repeatedly and the same if I try to update it manually, it says it can not find the file location of where to save the file, its time to do a clean install of ubuntu so I figure I will remove ubuntu completely then try to update the bios then install ubuntu again, do I need a usb windows recovery disc before I begin? what procedure is best to follow and in what order? I googled this and seen different methods and want to make sure I do not mess up my laptop.

I am going to upgrade 18.04 to 20.04 I know if I backup and restore some configuration files that it can mess up my new install so what files can I safely back up? pretty sure no hidden files in my home folder.

This is an hp laptop, I have been running ubuntu 18.04 on it without issues except for the bios issue and I recently installed different DE's which also are causing issues which I will not do again.

---

### Post by ipv on 2020-03-22
the thread title says remove 'buntu & keep 10 which seems appropriate for the bios update scenario, but i strongly recommend a complete format & then a re-install of 10.

get the bios update file which is usually an .exe / self-executing file from the laptop manufacturer's site & save it on a flash drive.

do a fresh 10 install. do not go online or else 10 will start updating windows. stay offline & plug in the flash drive with the bios file & then update.

some motherboards have the feature to update the bios from within the bios which is real good because in this process the bios update is not os dependent.

it would be more convenient if you could provide more information about the laptop model & if it came with 10 pre-installed. i hope i could help.

---

### Post by dragonfly41 on 2020-03-23
I would [research rEFInd]("http://www.rodsbooks.com/linux-uefi/") first.

Its menu has links to boot update as well as the links to loaders.

After installing rEFInd (if you choose to try this alternative) I recommend tweaking the refind.conf file found in /boot/efi/EFI/refind/refind.conf

---

### Post by P-I H on 2020-03-23
This is what I did. Had some problems to start with, but OK in the end. This was on a desktop with 2 NVme disks and 1 SSD disk.
Use the installed Windows to create the [COLOR=#000000]usb windows recovery disc[/COLOR]
I used Disks to unformat the SSD on which I installed Ubuntu after a number of tries to install W10.
[https://ubuntuforums.org/showthread.php?t=2438673](https://ubuntuforums.org/showthread.php?t=2438673)

---

### Post by wildmanne39 on 2020-03-24
Thanks everyone for your answers, I am currently deleting partitions, I have removed the Ubuntu partitions, do I also remove the EFI system partition since I am going to be reinstalling the MBR?

---

### Post by oldfred on 2020-03-25
Windows only installs in UEFI boot mode with gpt partitions.
Windows only installs in BIOS boot mode with MBR(msdos) partitions.
Ubuntu will let you install to either, but really should not.

If UEFI system better to use UEFI, but have seen multiple HP users have so many issues they reverted to MBR.
But if Windows pre-installed and newer system it is UEFI and your Windows Product key is in UEFI for reinstall.

Do not know HP specifically, but a few new systems now update UEFI from within Ubuntu with fwupd.
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

Most UEFI also allow update from either bootable DOS flash drive or directly from within UEFI with update file on a FAT32 formatted partition. With my motherboard I use my ESP as I made it larger & changed permissions to use it.

Where are you saving UEFI update file? UEFI only reads FAT32, or maybe all older FAT types.

---

### Post by wildmanne39 on 2020-03-25
> Do not know HP specifically, but a few new systems now update UEFI from within Ubuntu with fwupd.
I will give that a try, I ended up having to reinstall windows completely and I have tried several times and the UEFI/Bios upgrade still fails, I have Ubuntu Mate installed but far from being setup completely.

I am glad I did not remove the UEFI partition, I left it in place and I downloaded windows 10 onto a usb drive to reinstall windows and I did not have any trouble with the Windows Product key.

Thanks to everyone.

---

### Post by ipv on 2020-03-25
which hp model is this & did it come with 10 pre-installed?

every activated windows 10 machine has all activation details saved on the microsoft server so even if you do not have a product key during or post activation you need not worry.

the minute you go online windows will activate your machine.

if i was you i would wipe the hard disk clean, as in format the disk, delete all partitions & do a fresh install of 10 then do the bios upgrade.

it will take more time & effort on your part but i recommend starting from scratch.

---

### Post by wildmanne39 on 2020-03-25
> **ipv said:**
> which hp model is this & did it come with 10 pre-installed?

every activated windows 10 machine has all activation details saved on the microsoft server so even if you do not have a product key during or post activation you need not worry.

the minute you go online windows will activate your machine.

if i was you i would wipe the hard disk clean, as in format the disk, delete all partitions & do a fresh install of 10 then do the bios upgrade.

it will take more time & effort on your part but i recommend starting from scratch.

That is what I ended up doing but the bios upgrade still fails, I am going to mark this thread solved because I did get Ubuntu uninstalled and installed again, it has been years since I removed ubuntu and kept windows, it is much harder these days.

Thanks

---

