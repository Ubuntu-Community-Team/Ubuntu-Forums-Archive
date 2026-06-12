---
title: "Boot loader not working and Boot-Repair cannot remove grub"
date: 2017-01-06
forum: Installation &amp; Upgrades
---

### Post by dpurrington on 2017-01-06
I'm hoping to have a dual boot installation, with Windows 10 on the primary drive (sda) and Ubuntu on sdc. After installing 16.04.1 LTS, grub says it cannot load the partiiton. All I get is the grub rescue prompt.

I've tried reinstalling multiple times, and trying various approaches. I've tried using Boot-Repair (recommended approach) using the Live USB. At some point in the process it tells me to run these commands:
sudo chroot "/mnt/boot-sav/sdc6" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sdc6" apt-get install -fy
sudo chroot "/mnt/boot-sav/sdc6" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*

The first of these commands fails:
Setting up shim-signed (1.19~16.04.1+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.66.6+2.02~beta2-36ubuntu3.6) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed

Clicking "forward" on the dialog that showed the commands to paste into terminal, it says "GRUB is still present. Please try again."

My pastebin is here: [http://paste2.org/V602NZwZ](http://paste2.org/V602NZwZ)

Thanks in advance for any guidance!

-Dave

---

### Post by oldfred on 2017-01-06
It looks like you have an UEFI system, but Windows installed in MBR(msdos) partitioned drive with BIOS boot mode with Ubuntu also in BIOS/MBR boot mode.
But you booted live installer in UEFI boot mode. That may try to repair in UEFI boot mode, but you do not have the required ESP - efi system partition on sda. And then sda should have to be gpt partitioned.
So reboot live installer in BIOS mode, add Boot-Repair again & choose advanced options and choose Ubuntu install and sdc drive as location for grub, not any partition. You also want to repair Windows boot loader in sda, so you can directly boot Windows.

 Windows not detected by os-prober on sda1. 
Because of above warning, not sure if Boot-Repair in Advanced options will let you install a Windows boot loader to sda. Windows 8 or 10 uses fast start up which is always on hibernation. Grub will not boot hibernated Windows. And Windows updates may keep turning it on. So best to have a way to directly boot Windows, so keep Windows boot loader in sda, and set BIOS to boot sdc. 

        
 [URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

If Boot-Repair will not install a Windows boot loader you can do this once you boot Ubuntu or from live installer.

 Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader to boot partition with boot flag (Windows). 

OR:

 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 

[URL="https://sourceforge.net/p/boot-repair/home/Home/"]
[/URL]

---

