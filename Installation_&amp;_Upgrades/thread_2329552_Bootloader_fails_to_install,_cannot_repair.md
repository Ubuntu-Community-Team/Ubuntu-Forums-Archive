---
title: "Bootloader fails to install, cannot repair"
date: 2016-07-02
forum: Installation &amp; Upgrades
---

### Post by jase01 on 2016-07-02
Hello all,

I'm trying to install Ubuntu 16.04 alongside Windows 10 from a USB drive. The installation always crashes when trying to install the bootloader, regardless of what options I choose. The device is free of errors and the Ubuntu image md5 checks out.

 I was advised to come here with this report from Boot Repair, which I used from Ubuntu Live: [http://paste2.org/bgHj1czO](http://paste2.org/bgHj1czO)

If it's important, I don't remember if I installed windows in UEFI mode. I can't imagine I'd ever do otherwise, though, and I'm not sure how to find out once it's been done.

Thank you in advance!

Jase



EDIT: I forgot, if it helps, this is the terminal buffer that shows what I get when I try to run the copy/paste commands provided by Boot Repair:
```
[FONT=courier new]

ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb6" dpkg --configure -a
Setting up shim-signed (1.12+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.66+2.02~beta2-36ubuntu3) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed


ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb6" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 315 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.66+2.02~beta2-36ubuntu3) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up shim-signed (1.12+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)


ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sdb6" dpkg --configure -a
Setting up shim-signed (1.12+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.66+2.02~beta2-36ubuntu3) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed


[/FONT]
```

---

### Post by oldfred on 2016-07-03
You have Windows in BIOS boot mode on sdb, your 700GB drive.Windows only boots in BIOS boot mode from MBR(msdos) partitioned drives.
Your other drives are over the MBR max of 2TiB, so are gpt partitioned. Ubuntu can be installed in BIOS mode or UEFI boot mode on gpt drives. Where Windows only boots in UEFI mode from gpt partitioned drives.

But if using UEFI, you must have an ESP - efi system partition on the drive seen as sda. Ubuntu's version of grub2 only installs to the ESP on sda and will not correctly install anywhere else.
So you can create a FAT32 partition preferably at start of drive with boot flag. 300 to 500MB suggested.
I prefer to put both the ESP & a bios_grub partition as the first two partitions on every gpt drive, even my larger flash drives. Then I can configure for either UEFI or BIOS boot. Even if drive is currently planned as data drive I want an install of Ubuntu on it and boot files in the ESP. But if not sda, you have to leap thru hoops to get it to be bootable (copy files from sda's ESP to other drive's ESP).

Since Windows is BIOS, you can only dual boot from grub if Ubuntu is BIOS boot. You would then need a 1 or 2MB unformatted partition anywhere on drive that has bios_grub flag.

If you keep Ubuntu as UEFI and Windows as BIOS, you can only dual boot from UEFI boot menu or one time boot key like f10, f8 or f12 on most systems. Some require several keys.

You can also change order of drives in the SATA port order. I normally suggest Windows as first since it does not like to be anywhere else. But you have Windows on sdb. And then could have the UEFI boot drive of Ubuntu as sda. But that is defined by UEFI/BIOS and usually SATA port order.

---

### Post by jase01 on 2016-07-03
Thanks for the detailed response: I learned a great deal. 

Problem cause:
I had entirely forgotten that Win was installed in BIOS mode. The old mobo didn't support UEFI, and I didn't want to reinstall Win after replacing it. 


Solution used:
Fortunately for me, the fix is easy. This is an extra computer, so wiping it to reinstall Windows in UEFI mode isn't a problem. Then I will install Ubuntu alongside in UEFI mode as well.

---

