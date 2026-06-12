---
title: "Dual boot straight to Windows"
date: 2015-07-15
forum: Installation &amp; Upgrades
---

### Post by kevin171 on 2015-07-15
Hi,
I just completed a dual boot of Windows 7 and Ubuntu 14.04.2.  I installed a 3Tb drive and partitioned it for swap and ext4 with / on ext4 partition.  Everything went fine with the installation.  No errors but when I rebooted it went straight to Windows.  The Grub window did not even come up.  I have 3 drives installed sda, sdb and sdc.  My Linux install is on sda2 (sda1 is a small Windows reserve space).   Can someone help me out?

Thanks,
Kevin

---

### Post by oldfred on 2015-07-15
UEFI or BIOS.

It seems like you used Windows to partition 3TB drive. Windows only boots in UEFI mode from gpt and wants a system reserved space before the first NTFS partition.

If UEFI the first partition really should be an ESP - efi system partition.
And if BIOS you must have a bios_grub partition for grub to correct into to gpt partitioned drive.

Grub does default to installing to sda, but if you do not have either efi or bios_grub it will not install.

After you have added correct partition, you can use Boot-Repair to easily reinstall grub to 3TB drive. With multiple drives, do not use auto fix option. That installs grub to every drive. You need to use advanced option and choose install and choose drive. You want boot loader on same drive as install.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Partitioning on gpt drive. These should be first partitions on drive:

 gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by kevin171 on 2015-07-17
Thanks so much Fred.  I deleted the Windows reserve space and created and unformatted 2mb partition with boot grub flag.  Thanks for the mention of multiple drives...I checked my other disks and found there was a boot grub partition on one of the other drives as well.

Cheers!

---

