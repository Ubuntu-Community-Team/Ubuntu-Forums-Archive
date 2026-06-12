---
title: "Unable to Boot WIndows 8 OR Ubuntu"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by Rileymd on 2014-01-11
Hi,

A few months ago I successfully installed Ubuntu 13.04 on my Dell XPS 8700 desktop and was able to dual boot into either Windows 8 or Ubuntu without any problems. After upgrading to Windows 8.1 I no longer received the option to boot into Ubuntu and it would just automatically boot into Windows 8.1 so I created a bootable USB drive with boot-repair and repaired the boot file with the recommended settings. After doing this I could once again choose to boot into Ubuntu or Windows 8.1. This worked for 1 day and then the next day when I went to turn on my computer I received the following error:

No boot device available
Strike the F1 Key to retry boot, F2 to run the setup utility
SATA 0: Installed
SATA 1: Installed
SATA 2: None
SATA 3: None
SATA 4: None
MSATA1: None

Other notes:
-I did not receive a recovery CD with my computer and instead have a recovery partition
-The computer is only a few months old
-Secure Boot is now OFF in BIOs settings, however I believe I left it on before
-Here is a log from boot-repair: [http://paste.ubuntu.com/6732480/](http://paste.ubuntu.com/6732480/)

What I have tried so far:
-Opening up the computer and ensuring all the SATA cables were correctly seated
-Changing the BIOs settings to default
-Pressing F8 to boot into Dell Recovery Mode (it gave me the same error as above)
-Pressing F12 and Legacy booting from the HDD
-Ran boot-repair again with the recommended settings
-Ran boot-repair with the option to "Restore EFI backups"

If anyone could give me some other suggestions to help fix this it would be greatly appreciated!

Riley

---

### Post by oldfred on 2014-01-11
It looks like you have done the "buggy" UEFI rename. I do not think Dells need that. It is for those UEFI that the vendor modifies to only boot Windows. Or you never can use ubuntu entry in UEFI menu to boot.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

There is also a bug in grub that it will not boot Windows 8 or 8.1 from grub menu with secure boot on. So leave secure boot off, but UEFI on. Only systems installed in secure boot mode will be offered to boot from UEFI menu. You have Ubuntu installed in UEFI mode, but not secure boot mode.

Windows 8.1 mirrors the UEFI NVRAM data in BCD.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

Some need to add ubuntu to BCD then so NVRAM keeps entry.
      
 Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

