---
title: "Installing Ubuntu On A 128 GB Flashdrive"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2016-02-16
I installed Ubuntu on a 128 GB usb flashdrive with Win32 and when it gets to loading the GRUb I get the following error.  Also attached are photos of the problem reported to Ubuntu.  Does anyone know what could be going on?

---

### Post by oldfred on 2016-02-16
Is this a UEFI install on a UEFI system, but Windows on hard drive is in BIOS mode?

Post this from installer live mode:
sudo parted -l

---

### Post by sudodus on 2016-02-16
Please tell us more about your computer and your system, what you have and what you want. It will make it much easier for us to help you :-)

Specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- What is Win32? Do you mean 'Win32 Disk Imager'?

- From what did you install Ubuntu? Which version (Wily acccording to the attached picture)? 32-bit or 64-bit?

- Is the computer running in UEFI or BIOS mode?

- Do you want a single boot or dual/multi boot system installed in the internal drive?

- Do you want a system ('persistent live' or 'installed') in the 128 GB pendrive?

---

### Post by shane_faulkinbury2 on 2016-02-17
It's a stupid Dell Inspirion with 2 4GB DDR3, UEFI and I want it installed on the flash drive. I also have a dual boot with Windows 10 and Kali 2016!  It's Ubuntu 15.10.

---

### Post by sudodus on 2016-02-17
You may have problems to make an installed system in a USB pendrive survive in UEFI mode. Particularly if you don't want or can't use the EFI partition in the internal drive.

Maybe you can the systems described in the following links

[A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode]("http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506") and

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by oldfred on 2016-02-18
My Dell SFF small form factor system installed in UEFI mode very easily, but that was to same drive and I partitioned with gparted after using Windows to shrink the NTFS partition.

I have full installs in UEFI mode on flash drives. But always have had to manually partition, so I could have an ESP - efi system partition on the flash drive. But Ubuntu always installs grub to drive seen as sda. You must have ESP on drive seen as sda and then copy /EFI/ubuntu to sdb and copy again to sdb as /EFI/Boot. Then rename shimx64.efi to bootx64.efi. UEFI only boots external drives from a FAT32 formatted partition with the boot flag or ESP and from /EFI/Boot/bootx64.efi.

---

### Post by shane_faulkinbury2 on 2016-02-18
Thanks oldfred, I'll try that out and see if it works!  ;)

---

### Post by oldfred on 2016-02-18
This is an older install, I think I have another somewhere also.
Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1025484   499.7 MiB   EF00  efi64
   2         1026048        44033860   20.5 GiB    8300  System64
   3        44034048       120997887   36.7 GiB    0700  data
fred@A105-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2        21G  3.8G   16G  20% /media/fred/vivid64
/dev/sdb3        37G   12G   24G  33% /media/fred/data64
/dev/sdb1       499M  5.6M  494M   2% /media/efi64

I think I made ESP, sdb1 a little large.
It looks like I renamed grubx64.efi. Which also works as long as you never turn on secure boot.
fred@A105-Precise:/media/efi64/EFI/Boot$ ls -l
total 2260
-rw-r--r-- 1 fred fred  958328 Apr  8  2015 bootx64.efi
-rw-r--r-- 1 fred fred 1355736 Oct  8  2014 shimx64.efi
fred@A105-Precise:/media/efi64/EFI/Boot$ ls /media/efi64/
EFI
fred@A105-Precise:/media/efi64/EFI/Boot$ ls /media/efi64/EFI/ubuntu -l
total 3428
-rw-r--r-- 1 fred fred     126 Apr 24  2015 grub.cfg
-rw-r--r-- 1 fred fred     126 Apr 24  2015 grub.cfg~
-rw-r--r-- 1 fred fred  958328 Apr 24  2015 grubx64.efi
-rw-r--r-- 1 fred fred 1264848 Apr 24  2015 MokManager.efi
-rw-r--r-- 1 fred fred 1276984 Apr 24  2015 shimx64.efi

The version of grub that install puts into the ESP on sda or internal drive, expects to find /EFI/ubuntu/grub.cfg, so that is why you also need /EFI/ubuntu folder. 
You can install grub directly with the removeable parameter and that creates a different version of grub and renames it bootx64.efi. But other manual maintenance required for a full install.

---

