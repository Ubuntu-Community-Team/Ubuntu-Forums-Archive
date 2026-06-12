---
title: "Unable to boot after reinstallation of Ubuntu"
date: 2019-07-07
forum: Installation &amp; Upgrades
---

### Post by akshay_c11 on 2019-07-07
Hi,
I had a previously working dual-boot of Windows 10 and Ubuntu 16.04. I remember having to jump through some hoops to get it dual booted then, but it's been a while, and I can't remember the exact steps I took then.

When I tried to update the 16.04 to 18.04 using an install disk, It went nearly all the way to the end, but failed at updating the GRUB / bootloader
Stage of failure:
```

Installing the grub2 package
The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB bootloader, the installed system will no boot.

```
When I reboot, I keep getting into grub-rescue.

In there, I tried to do the following:
```

set prefix=(hd0,6)/boot/grub
set root=(hd0,6)
insmod normal

```
However that gave the error "normal.mod not found"

So, following some instructions online, I booted up the live image again, and installed boot-repair following the steps specified in [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

When I run boot-repair and select the `recommended` option, I get a window asking me to  run the following commands:
```

sudo chroot "/target" dpkg --configure -a
sudo chroot "/target" apt-get install -fy
sudo chroot "/target" apt-get purge -y grub*-common grub-common:i386 shim-signed

```

However, on running those, I get the following:
```

ubuntu@ubuntu:~$ sudo chroot "/target" dpkg --configure -a
Setting up grub-efi-amd64-signed (1.93.14+2.02-2ubuntu8.13) ...
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
ubuntu@ubuntu:~$ sudo chroot "/target" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 689 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.93.14+2.02-2ubuntu8.13) ...
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


Pastebin from boot-repair: [http://paste.ubuntu.com/p/QP6ZFTvnxt/](http://paste.ubuntu.com/p/QP6ZFTvnxt/)

Any help with this would be highly appreciated. 

Thanks

Akshay

---

### Post by jeremy31 on 2019-07-07
Disable EFI in UEFI/BIOS, then install Ubuntu 18.04 or try boot repair after disabling EFI.  Your disks are not formatted for using EFI

---

### Post by akshay_c11 on 2019-07-07
Ahh.. I see.. that worked... thanks a lot

---

### Post by Artim on 2019-07-07
Don't forget to mark this thread [SOLVED] so that others may benefit from your question and the solution!

---

