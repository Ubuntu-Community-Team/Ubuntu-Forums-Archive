---
title: "Install 13.10 suceeds, grub2 works, then dissappears"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by Tom McD on 2013-10-20
Installed 13.10 lastest-nightly (10-16-2013) and was sucessful to sdc. After restarting the computer without the USB live disk, it sucessfully brought up the grub2 boot menu. Was able to secure boot Ubuntu 13.10 on my HD. Restarted the computer, and was able to select Win8 and secure boot it from grub2.

2 hard drives, UEFI.  Intel SRT disabled in bios. Win 8 fast-restart disabled.

After shuttng down Win 8 and repowering on the computer an hour later, there is no boot on sdc, and only windows boot manager on sda. No evidence of grub2 anywhere. F12 starting in BIOS shows only the win boot Mgr on sda, nothing bootable on sdc.

Rebooted from USB live UEFI. command-line Loaded boot-repair and ran.

It says:  EFI detected, check options.

If I click recommended boot repair, it says "Please disable SecureBoot in the BIOS. then try again."
Since win 8 must boot in secure mode, this seems wrong.

here is the boot configuration:

[http://paste.ubuntu.com/6272576](http://paste.ubuntu.com/6272576).

sda is 2T HD with windows
sdc is 2T hD with Ubuntu 13.10
sdd is the USB live stick.

Not sure how to proceed forward at this point.

-- Tom

---

### Post by oldfred on 2013-10-20
Windows 8 should not require secure boot, although a few pre-installed systems do seem to require it or users have not turned it off correctly.

You are showing the RAID again which would be from Intel SRT. But that will continue to confuse anything related to installing grub or mounting NTFS partitions. You should not mount Windows main partition anyway or possibly in read only mode.

Grub is in the efi partition in sda1 and should boot. You have installed with secure boot on, so it also has the signed kernel and will boot with secure boot on.

---

### Post by Tom McD on 2013-10-20
Thanks oldfred.  I see looking back at the pastebin that grub is installed on sda1.

Still, when I boot up, "Windows Boot Manager" is the only item listed as bootable in the BIOS,
and allowing it to boot brings up Windows 8 immediately.  How do I get it to bring up grub2?


-- Tom

---

### Post by oldfred on 2013-10-20
You should have an ubuntu entry even with secure boot on. 
Does it show ubuntu entry with secure boot off?

Only secure boot entries will show with secure boot on. But it looks like Ubuntu is installed insecure boot mode.

But a few UEFI have been modified to only boot Windows efi file. That is not per UEFI standard and not all systems seem to have that issue.
If you can boot Ubuntu without secure boot on, I would just do that.
But Boot-Repair has a work around for the buggy UEFI. It renames grub2's shim file which has the Microsoft signing key to hae the Windows efi file name. And then from grub you can boot the renamed/backed up Windows efi file. 
There is a bug where grub will not chain load to Windows with secure boot on. 
So you can rename file, boot directly from UEFI, or install rEFInd which some have said works.

       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

    
 Alternative efi boot Manager for UEFI limited systems:
[https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd](https://wiki.archlinux.org/index.php/UEFI_Bootloaders#Using_rEFInd)
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)
More info on secure boot - Ubuntu's shim may need changing to work with Refind
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

      
 Secure boot
[http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

 Rename option now under advance choices - updated Boot-Repair so that by default it will put grub/shim in EFI/BOOT/bootx64.efi only
[http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984](http://ubuntuforums.org/showthread.php?t=1769482&p=12740984#post12740984)
 available as a "Rename Windows EFI files" option in the Advanced Options for the few UEFI that are modified to only Boot Windows efi file.
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
      
 
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

 Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi.
/EFI/Microsoft/Boot/bkpbootmgfw.efi

---

### Post by Tom McD on 2013-10-22
Took some detective work...    I took out the Windows Hard Disk (HD), 
leaving only the Ubuntu HD plugged in. Reinstalled 13.10.  The installer
did the right thing and installed the boot partition on the HD, seems to work fine.
power down, power up, boot fine.

Unplugged Ubuntu HD, plugged in Win HD.  Win 8 boots fine.
Can swap back and forth between the two, whichever HD is plugged in boots fine.

Then, plugged both HD back in at the same time, powered up, but stopped at the
 boot menu (F12). Win Boot Manager available, but no Ubuntu boot found.

Immediate power down prior to actually booting.

Unplugged Win 8 HD, leaving only Ubuntu HD.  Powered back up - no bootable devices found.

It appears that the BIOS itself as soon as it sees any Windows Boot Manager partition writes
false to the boot flag on all the other Hard Drive bootable partitions.

I was able to resuscitate the Ubuntu HD using boot repair. I captured the boot signatures in both
the bootable and unbootable states and they appear identical. Don't see where the boot flag is
displayed from boot-repair.

bootable - paste.ubuntu.com/6278847
not bootable - paste.ubuntu.com/6285903

I am not sure boot repair lets one look at the boot flag.  Gparted does let one look at the boot
flag, so the next time may be able to resusciate just by setting it on the Ubuntu HD.

For now, seems the only solution is to never have the Win HD and the Ubuntu HD plugged in
at the same time.

-- Tom

---

### Post by oldfred on 2013-10-23
UEFI does not have a boot flag. It searches the efi partition but which in gparted is set as efi partition GUID by using boot flag. Not the same as BIOS boot flag which is a flag in the partition table.

UEFI should find both drive's efi partition and Boot-Repair will add a chainload entry in grub2's menu to boot Windows in a different efi folder/drive.

If secure boot is on, UEFI only shows the systems that are secure boot. 
You may have in UEFI menu both UEFI on but secure boot off and CSM/BIOS/Legacy boot UEFI menu options. Some systems seem to only have secure boot on or off and will boot in UEFI or BIOS depending on what is found.

You seem to have the Ultrabook type small SSD that is using RAID (somehow) to cache Windows. That RAID confuses grub as it should install inside the RAID, but with SRT it really is a standard efi partition that you would install into.
I also do not think Grub can chainload to a Windows with its fastboot on and some have reported that the fastboot setting resets Windows as default boot anyway.

More info on Intel SRT and dual drive installs in various links from link in my signature.

---

