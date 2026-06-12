---
title: "Problem with UEFI installation."
date: 2013-01-16
forum: Installation &amp; Upgrades
---

### Post by TheMophead on 2013-01-16
Hello,

In the past I've dual booted systems without failure, even managed to triple boot at one time, but I'm having a bit of an issue.

I purchased a laptop that came pre-installed with Windows 8. I thought it'd be a good idea to install Ubuntu as I've done on countless other laptops before. I booted up Ubuntu from a LiveUSB, opened GParted, resized Drive C: and created a new partition for Ubuntu. I installed Ubuntu into this Partition and every thing works great, however, I have a little problem.

In GRUB2, when I select Windows 8, I get this error:

```
error: unknown command 'drivemap'
error: invalid EFI filepath
```

I can boot into Ubuntu fine and everything is ok, but this problem still persists. At this point I can get back into Windows but this is done by me going back into the UEFI Boot Menu and changing the boot order, from then Windows automatically fixes what it thinks is a problem with it's installation.

I'm really stuck here and this is preventing me from using one of my favorite Operating Systems.

I'm using a Lenovo G580 with an i5-3210m and 8GB of RAM.

Any help would be greatly Appreciated. :sad:

---

### Post by oldfred on 2013-01-16
Did you install Ubuntu 64bit 12.10 in UEFI mode or BIOS/Legacy mode? To be able to dual boot from grub menu you have to have both systems in UEFI. And grub2's os-prober has a bug that does not create correct chain load entries.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vitial for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Some Lenovo's have issues.
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)
[http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)
    
Others have worked:
       Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
    
Some of the work arounds to get systems that only boot Windows in UEFI mode are to backup the Windows efi file, and copy & rename a grub or shim file to the Windows name. Then grub chain loads back to the Windows backup to dual boot.

       sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)

            To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

