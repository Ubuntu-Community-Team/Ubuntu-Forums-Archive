---
title: "invalid partition table on dev sda wrong signature 0"
date: 2022-07-16
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-07-16
PC with problem is more than several years old.  All its life, it has been running dual boot with Win 10 Pro and constantly upgrade versions of Ubuntu.  Current version is Unity build of 22.04 LTS.  I shut the PC down for two weeks of holiday.  When I returned, I turned it on and was busy with turning other systems on and had not noticed it had booted straight into Windows.  When I had the chance, I ran gparted, as failure to boot into Ubuntu is often due to corruption of ext4 partitions caused by Windows 10.

When I ran gparted, I did not perform as expected but gave the error, "invalid partition table on dev sda wrong signature 0".  SSD is Intel SSDSC2BP480G4.  All data are in exfat partitions and are backed up on a commercial off-ste service.

Windows disk management says everything okay.

How do I go about fixing this problem?

Thank you,

John

---

### Post by ubfan1 on 2022-07-16
Is the disk partitioning GPT or MSDOS, and are the Windows/22.04 installs in UEFI mode or legacy?  Windows in UEFI mode requires a GPT disk, but Ubuntu doesn't care.  A GPT disk will have a backup partition table at the end, so that might be useful.  Do you have a record of the partition start/end in sectors?  If so, it may be typed in again with gparted, but first before anything else, ensure your backups are restorable ;^)  Things can go badly wrong when editing partition tables.

---

### Post by cigtoxdoc on 2022-07-16
Thank you for your help.

The PC in question was home-built from commercial motherboard and case, probably around 2014.  When I needed a new SSD, I suspect I backed up everything on a USB storage drive, and installed Win10 Pro from the startup USB I had purchased from Microsoft.  So, I don't know if it is MS-DOS or GPT partitioning.  As I got more into Ubuntu, I added Ubuntu to the system and have been upgrading  it as new releases were issued.  More recently, I used gparted to make exfat partitions so that data would be fully accessible to both Windows and Ubuntu.  Operation under Win 10 Pro is perfect; and since I have more than several PowerPoint presentations to do in the next few weeks; and meeting sponsors require PPTX.  Thus, there is no need to do anything immediately.  All my email is IMAP, so Outlook 365 does the same thing as evolution on my laptops.  One of them is a hp840g1, and it works fine of both OS's. 

So, if the disk was originally formatted with the Win 10 Pro USB, is it MS-DOS partitioned or GPT partitioned.

John

---

### Post by ubfan1 on 2022-07-16
I don't know what the Windows Installer does, but take a look at the partitions from Windows.  If you have an extended partition (and logicals within it), you have an MSDOS partitioning and Windows in legacy mode. GPT does not require the extended/logical partitions, is slightly more compact (less space between partitions, and as a result, there is no room for an MSDOS boot sector after the partition table, so an explicit bios-grub flagged partition (1-2MB, unformatted), is necessary to hold the legacy  bootloader.  UEFI has all the bootloaders in an EFI FAT partition, and they are just files, so UEFI may be used on either an MSDOS or GPT partitioned disk (but usually UEFI and GPT go together since they are more modern).

---

### Post by cigtoxdoc on 2022-07-16
Thank you for your additional help.  I don't know what I am doing, so I have attached a jpg showing the output of Win 10 Disk Management program. I suspect that Partition 11 is where the Ubuntu OS is.

The big question here is if I put the Ubuntu (unity) 22.04 Live USB in and boot from it, what will happen?  Will it see the invalid partition table and say I can't do anything or ask me to do something I do not know how to do?

John

---

