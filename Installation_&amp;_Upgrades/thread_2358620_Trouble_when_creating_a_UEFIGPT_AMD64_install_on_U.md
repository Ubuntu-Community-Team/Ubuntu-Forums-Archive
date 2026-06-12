---
title: "Trouble when creating a UEFI/GPT AMD64 install on USB-drive"
date: 2017-04-15
forum: Installation &amp; Upgrades
---

### Post by Cbhihe on 2017-04-15
Hi, I am trying to create a bootable USB drive to later use it to install UbuntuGnome 17.04 on UEFI/GPT.

I am following @sysmatck 's ancient but very informative [guide]("https://ubuntuforums.org/showthread.php?t=2276498&") and have browsed various posts ([example]("https://ubuntuforums.org/showthread.php?t=2281452")) that seem related. 

What I need is rather simple. Creating a multiboot Grub2 based USB-drive  setup is really for learning purposes, as I do not need the multiboot  functionality right now. What I do need on the other hand is:
- to be able to install Ubuntu (from that USB drive) on various boxes' internal UEFI/GPT storage volume, 
- to be able to boot a live USB instance of Ubuntu,
I also need Gparted to be included in the official ubuntu-gnome-17.04-desktop-amd64.iso. I imagine it is so by default.

What I have done so far: 
- clean wipe of 2GB USB drive
```
$ sudo sgdisk --zap-all /dev/sdb
```

- creation of new partition /dev/sdb1, starting at boot sector 0, with hex type code "ef00"
```
$ sudo sgdisk --new=1:0:0 --typecode=1:ef00 /dev/sdb

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! Main and backup partition tables differ! Use the 'c' and 'e' options
on the recovery & transformation menu to examine the two tables.

Warning! One or more CRCs don't match. You should repair the disk!

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Could not create partition 1 from 3930112 to 3932126
Error encountered; not saving changes.

```

- In spite of that, I tried formatting anyway...
```

$ sudo mkfs.vfat -F32 -n GRUB2EFI /dev/sdb1
mkfs.fat 3.0.26 (2014-03-07)
...
Found invalid GPT and valid MBR; converting MBR to GPT format in memory. 
***************************************************************

Exact type match not found for type code 7200; assigning type code for
'Linux filesystem'
Exact type match not found for type code 6500; assigning type code for
'Linux filesystem'
Exact type match not found for type code 7900; assigning type code for
'Linux filesystem'
Exact type match not found for type code 0D00; assigning type code for
'Linux filesystem'
Warning! Main partition table overlaps the first partition by 34 blocks!
You will need to delete this partition or resize it in another utility.

Warning! Secondary partition table overlaps the last partition by
3801977530 blocks!
You will need to delete this partition or resize it in another utility.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
GPT data structures destroyed! You may now partition the disk using fdisk or
other utilities.


```

So I went to Gparted and reformated with GPT and FAT32 and got:
[IMG]https://drive.google.com/open?id=0B96LA3GJ6wE1bU1ZVC1acG5MTmc[/IMG]

In spite of the errors visible in Gparted output above, I could mount  the newly formatted volume (with sudo) and delete a "lost+found"  directory on it.


I don't quite understand the reason for the above error reports and how I can go about solving them.
And I have not even started to deal with the ISO file !... 

Any detailed help greatly welcome. Cheers.

-ced

---

### Post by oldfred on 2017-04-15
If just a 2GB flash drive I would probably stay with MBR(msdos). I do not think 2GB is large enough for multiple booting ISO.
I do only use gpt on all my larger flash drives and have either full installs with additional ISO to boot using grub, or just grub directly booting ISO.

I have seen a few comments where some systems do not like to boot gpt partitioned drives.
Also issues with some flash drives, some installers and which port is bootable on a pc.
I have never had issue, but many have various issues and changes to flash drive, flash drive partitioning & other configurations usually get it to work.

Windows does not correctly convert a gpt partitioned drive to MBR, so it leaves backup gpt partition table. Then Linux tools see MBR & backup gpt and get confused. Usually best to just start over.

Mounting a MBR partitioned drive with gdisk or sgdisk will in memory convert to gpt. Only if saved will it actually convert. But if you want MBR, best not to use gdisk. I typically use gparted.

If you only want UEFI (not BIOS).
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

For Multiple boot. UEFI is a bit more difficult as you have to partition in advance, make sure you have ESP on flash drive, but grub only installs to ESP on drive seen as sda. You then copy /EFI/ubuntu twice from ESP on sda to flash drive. Once to /EFI/ubuntu and to /EFI/Boot and rename shimx64.efi to bootx64.efi.
External drives with UEFI only boot from /EFI/Boot/bootx64.efi. And full install version of grub expects more files in /EFI/ubuntu, so both copies required.

       
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

If only grub and not also full install:
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

  How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images, manual grub install
[http://ubuntuforums.org/showthread.php?t=2276498](http://ubuntuforums.org/showthread.php?t=2276498)

---

### Post by Cbhihe on 2017-04-15
Thank you @oldfred. 

I just need a UEFI-only boot, so following your answer, I set the boot flag to "boot".

I assume this should allow me a clean install of the content of the  iso file onto the machine I want to set up. This is what I want to do  after partitioning its internal storage.

 I have a doubt though, since I had already copied [FONT=courier new]boot[FONT=arial] and[/FONT][/FONT] [FONT=courier new]EFI[/FONT] directories onto the flash drive, following @sysmatck 's guide, should I remove all that prior to booting from this USB drive on a UEFI machine ? 
This would leave me with the plain iso file there on that flash drive. Correct ?

---

### Post by oldfred on 2017-04-15
The install ISO file has its own /EFI/Boot/bootx64.efi that is a minimal grub just to boot the flash drive install. Nothing else is required with standard installer.
It just is if you want to directly boot ISO, then you have to install your own copy of grub. But then grub & ISO can be in same FAT32 folder. 
Getting grub installed and grub.cfg correct with path to location of ISO and drive like hd0,1 are the main issues of direct ISO boot. 
Some distributions require extraction of ISO boot files to boot ISO, but not Ubuntu.


If BIOS boot required the syslinux is in MBR and PBR and has its own boot configuration files in flash drive. Typical installers for Ubuntu configure/install the syslinux boot loader in addition to formatting flag drive, setting boot flag, and extracting ISO to flash drive.

---

### Post by Cbhihe on 2017-04-16
I exchanged my Flash drive for another one. As a result the earlier MBR / GPT mixup has gone away.

Next I formatted the drive with  GPT / Fat32 and copied the official [FONT=courier new]ubuntu-gnome-17.04-desktop-amd64.iso [FONT=arial]on it. I then set the partition's flag to [/FONT][/FONT]"boot" (/dev/sdX1).

The machine to boot from flash drive is a  Dell XPS 15 9360 series with the following USB config in BIOS settings::
- "Boot sequence" does not include Window Boot Manager
- Boot list option is (factory default) set to UEFI

- "Secure boot" disabled
- Enable Boot support
- Enable TB ports
- Always allow Dell docks
- Enable external USB port
- Enable TB boot support
Security level - User authorization (default)

[B]PATH 1
[/B]- "AHCI" SATA operation
- "Enable UEFI network stack" boot ("Legacy boot" disabled)
- UEFI boot path security : always

Note:  After several unsuccessful attempts at booting from the flash drive, I  noticed there is a directory hierarchy next to the iso:  EFI/Dell/logs/diags_current.xml. I vim'ed into the xml file. It appears  to be an event log showing low battery charge warning, etc. It got  written to the flash drive tree during the boot attempt.

Error message (*approx wording*): "There is no boot device detected. Press any key to restart."
I don't seem to be making much progress.

**PATH 2**
Press F12 to enter boot's "one time menu" during initial boot sequence
- Enabled legacy boot + exit
- restart +  F12 + boot menu indicating new "Legacy boot" section:
       - M.2 PCIe SSD
       - "USB storage Device" <<<< I selected that with the flash drive plugged in.
Error message: Selected boot device failed. Press any key to reboot the system."
I am stuck here. Can somebody walk me through this. I have read tens of pages of doc and posts on this...

---

### Post by oldfred on 2017-04-16
Did you copy ISO or extract ISO.
An extracted ISO has all the files & folders needed to boot in UEFI mode if on FAT32 formatted partition with boot flag.
Your UEFI should show a boot option for UEFI flash drive. You may have to turn on allow boot from USB ports somewhere in UEFI.

Some with Dell have posted they have to have legacy on, but still boot in UEFI mode. Almost all other systems the legacy/UEFI switch(s) is how you boot.
Dell somehow may have some drivers in the CSM mode usable with UEFI??

A copied ISO needs grub and you have to manually create your own grub.cfg that uses the loopmount feature of grub to directly boot any ISO that is designed for loopmounting. The full Ubuntu ISO can be loopmounted. The mini-ISO was not that configuration a year or two ago.

---

### Post by Cbhihe on 2017-04-16
pfff.... I had copied it (following instructions to which I referred in OP). I realize my mistake and your explanation makes sense. I'd need a grub.cfg to work with a copied ISO. Sorry... too many hours and too many posts read on this... I kinda saturate.
[FONT=arial]
So I reformatted the Flash drive one umpteenth time MBR/FAT32 this time and tried to extract the ISO to it. 
Working from Ubuntu 14.04.5
  - dble clicked on[/FONT] [FONT=courier new]ubuntu-gnome-17.04-desktop-amd64.iso[FONT=arial] file
  - selected the mounted Flash drive as "Disc to write to". (Drive is mounted directly on /mnt). 
Error message: Please replace the disc with a supported CD or DVD.

So this does not let me burn on Flash drive ?
[/FONT][/FONT]

---

### Post by oldfred on 2017-04-16
You probably do not have permissions in /mnt.
I use /mnt/data for all my data, but have to use commands to reset ownership & permissions to similar to /home's permissions.
If you just click on flash drive with Naulitus file browser it should default mount to /media/$USER/something and then you have permissions to copy.

---

