---
title: "D partition appears as free space?"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by ArFat on 2012-10-15
Hi all,
I'm trying to install dual boot Ubuntu with Windows 7.
Windows 7 is installed first, I have to partition in Windows OS C: (NTFS - system partition) and D: (NTFS - archive partition) and I enter to disk management and create a free space allocated space.
When I enter ubuntu CD to install it, it shows me only C partition and D partition appears as free space (allocated space)...
My question is: If I create a new linux partition (ext3) does it destroy D partition on Windows OS ?
if it does, how to install without loosing data on C and D partitions ?

Thanks in adcance

---

### Post by spjackson on 2012-10-15
This doesn't sound right. Can you please post screenshots from both Disk Manager in Windows and Gparted in Ubuntu?
Also post the output of
```

sudo fdisk -l

```

---

### Post by Bashing-om on 2012-10-15
ArFat; Hi ! Welcome to the forum .

How old is your machine ? Lately things have got more complex dual booting with windows. The possible issues of GPT partitioning and UEFI need now to be explored.

If you plan to dual-boot, how is Windows booting, in BIOS mode or in EFI mode? You can find out by typing "bcdedit" in a Windows Administrator Command Prompt window and looking for the "path" line in the "Windows Boot Loader" section. If this line refers to winload.efi, then you're booted in EFI mode; if it refers to winload.exe, then you've booted in BIOS mode.


If GPT is detected: Will have to create a BIOS-Boot partition (>1MB,unformatted filesystem, bios_grub flag). This can be performed via tools such g-parted.

these links provide instruction if UEFI:
[http://ubuntuforums.org/showthread.php?t=2059640](http://ubuntuforums.org/showthread.php?t=2059640)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://ubuntuforums.org/showthread.php?t=2064761](http://ubuntuforums.org/showthread.php?t=2064761)
[https://gitorious.org/tianocore_uefi_duet_builds/pages](https://gitorious.org/tianocore_uefi_duet_builds/pages)

else: if we are dealing with the older msdos [bios](ubuntu MBR) format..things are straight forward - but can have but  a maximum of 4 primary partitions per disk and windows generally uses up all 4 of them; there are ways to free up a partition to install ubuntu to.

please to advise us of how your system is presently formated. Further assistance pending this information.[INDENT]try'n to help <==BDQ

[/INDENT]

---

