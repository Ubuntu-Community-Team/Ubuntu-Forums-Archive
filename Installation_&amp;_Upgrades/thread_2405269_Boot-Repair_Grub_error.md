---
title: "Boot-Repair Grub error"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by bat2018 on 2018-11-03
Hi,

I am trying to install a dual boot, with windows 10, i have come across an error while using boot-repair. Can any one help out?

```

ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" dpkg --configure -a
Setting up grub-efi-amd64-signed (1.93.8+2.02-2ubuntu8.7) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 280 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.93.8+2.02-2ubuntu8.7) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" dpkg --configure -a
Setting up grub-efi-amd64-signed (1.93.8+2.02-2ubuntu8.7) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda3" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 280 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.93.8+2.02-2ubuntu8.7) ...
Installing for x86_64-efi platform.
grub-install: error: cannot find EFI directory.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by oldfred on 2018-11-03
Post link to the Summary Report (not report) that Boot-Repair gives.

---

