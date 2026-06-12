---
title: "Windows + Ubuntu 16.04 dual boot problems"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by jmoney2 on 2017-01-01
Hi,

I recently tried to dual boot my existing Windows 10 PC by installing Ubuntu 16.04 alongside it in a dual boot configuration - however I think during the installation process I setup Ubuntu as a Legacy install instead of UEFI as I can now boot into Ubuntu great, but have no ability to select to boot into Windows.

I've gone through a few online tutorials to try and use boot-repair to switch, but when I run through the recommended remediation, boot-repair prompts me to run some commands on the command line, and these give errors in the terminal:

What it asks me to run:
```
sudo chroot "/media/ubuntu/1fbf1d9f-cda3-40d1-bc46-b726ed09efb4" dpkg --configure -a
sudo chroot "/media/ubuntu/1fbf1d9f-cda3-40d1-bc46-b726ed09efb4" apt-get install -fy
sudo chroot "/media/ubuntu/1fbf1d9f-cda3-40d1-bc46-b726ed09efb4" apt-get purge -y --force-yes grub*-common grub-common:i386 shim-signed linux-signed*
```

The output in terminal:
```
ubuntu@ubuntu:~$ sudo chroot "/media/ubuntu/1fbf1d9f-cda3-40d1-bc46-b726ed09efb4" dpkg --configure -a
Setting up shim-signed (1.19~16.04.1+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up grub-efi-amd64-signed (1.66.2+2.02~beta2-36ubuntu3.2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 shim-signed
 grub-efi-amd64-signed
ubuntu@ubuntu:~$ sudo chroot "/media/ubuntu/1fbf1d9f-cda3-40d1-bc46-b726ed09efb4" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 326 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.66.2+2.02~beta2-36ubuntu3.2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up shim-signed (1.19~16.04.1+0.8-0ubuntu2) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package shim-signed (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've included a link to my boot-info pastebin dump, in the hope that someone can identify what is wrong here and help me out!
Boot-info: [http://paste2.org/Ek7CX9nD](http://paste2.org/Ek7CX9nD)

Cheers

---

### Post by oldfred on 2017-01-01
While you have UEFI based hardware, both Windows & Ubuntu are installed in BIOS boot mode and MBR(msdos) partitioning on sdb. And sda is also partitioned with MBR, not the newer gpt.

But you booted Boot-Repair in UEFI boot mode. Best if systems are BIOS/MBR to boot Boot-Repair in BIOS mode.

Did you leave Windows 10 fast start up on (always on hibernation)? Or resize Windows with gparted. Windows always needs chkdsk after a resize or often after any issue.

Best to have Windows repair/recovery flash drive.

Do not run Boot-Repair's auto fix. Than installs grub to every MBR. May be better to have grub in sda and have BIOS boot sda by default, and keep the Windows boot loader in sdb. Then when Windows has issues, you may be able to directly boot it. You can use Boot-Repair's advanced mode to choose a system and then a drive for boot loader. Put grub on sda, & Windows on sdb.

You may have to install a Windows or Windows type boot loader to sdb so you can boot Windows. Grub only boots working Windows, or Windows that does not need chkdsk, nor is hibernated.
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by jmoney2 on 2017-01-02
Nice! Thanks for the help oldfred, this worked perfectly.

The solution for me was:
1. Boot off my live ubuntu USB drive from non-uefi mode
2. Do the boot-repair installation process
3. Setup sda as the location for grub, and remove grub from sdb
4. Wait a few minutes for boot-repair to do its thing

Worked like a charm, and now I actually have a working boot loader screen if I boot to SDA! Awesome.

---

