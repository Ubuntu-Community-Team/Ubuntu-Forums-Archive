---
title: "Boot problem after installing Ubuntu 13.10 alongside Windows 8.1"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by kuehn.marcel on 2013-12-21
Hello everybody,

I just installed Ubuntu 13.10 alongside the pre-installed Windows 8.1 on my Sony Vaio SVP1321L1EBI. The installation ran smoothly (deactivated fastboot and secureboot or whatever it's called), but I couldn't, at first, decide which OS I want to run when booting. It just directly booted into Windows 8.1. So I ran Boot Repair with my Live USB. 

First thing I got was "EFI detected. Please check the options." . After that I just ran the recommended repair. At the very end it asked something along the lines "WINefi detected. Do you want to activate..." and I pressed YES.

Now I can't boot anything. Tried some other options but still no success. Any idea how to fix this?

Heres the link I received the last time I ran Boot Repair: [http://paste.ubuntu.com/6615099/](http://paste.ubuntu.com/6615099/)

Thanks a lot!

---

### Post by fantab on 2013-12-21
Check in your UEFI/BIOS to what OS is booting first, It should boot 'Ubuntu' from /dev/sda3 or the third partition on your HDD.
Tell us if you can boot Ubuntu.
Change the boot order in UEFI to Windows and tell us if you boot windows.

---

### Post by oldfred on 2013-12-21
Boot-Repair ran its rename & backup. That is for those UEFI that are hard coded to only boot Window internally in UEFI. If you can boot the ubuntu entry from UEFI, you should undo the rename.
Also it looks like you booted Boot-Repair with secure boot on. It then installed the secure boot versions of grub & kernels. But there is a bug in grub that will not let you boot Windows from grub with secure boot on. Best to then have secure boot off.

       Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

   With the renamed file you cannot directly boot Windows from UEFI menu as it really is shim.
And a Windows update may rewrite the bootmgfw.efi file overwriting the shim version, so then if you can only boot the Windows version you have to rerun boot repair. If you can boot Ubuntu entry in UEFI menu, undo the rename.

   To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.


 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

### Post by kuehn.marcel on 2013-12-22
Hey,

it works now. I thought I tried it already, but I did it again today (no secureboot checked in boot repair) and now it's working.

Thanks!

---

### Post by fantab on 2013-12-22
> **kuehn.marcel said:**
> Hey,

it works now. I thought I tried it already, but I did it again today (no secureboot checked in boot repair) and now it's working.

Thanks!

That's great.
You can mark the Thread as 'Solved' using Thread Tools.

---

