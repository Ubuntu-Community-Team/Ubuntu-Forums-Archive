---
title: "GRUB issue blocks apt/dpkg after update to 19.10"
date: 2019-12-07
forum: Installation &amp; Upgrades
---

### Post by vatharian on 2019-12-07
Hello!
I'm running Ubunru 19.04, now freshly updated to 19.10. And now I can't get apt to behave.

First, I have an issue with grub:
```
grub-install: warning: Cannot read EFI Boot* variables.
grub-install: warning: efivarfs_get_variable: read failed: Interrupted system call.
grub-install: warning: efi_get_variable: ops->get_variable failed: Interrupted system call.
grub-install: error: failed to register the EFI boot entry: Interrupted system call
```

This comes from the fact, that my motherboard (Intel's S5520HC and -UR) has UEFI boot settings set as read only from 'outside' of IPMI or UEFI setup (I have to manually create boot entry with path to grubx64.efi). So far, I somehow was able to live with that, but now I can't use apt anymore, since it just borks out at the grub, despite not being asked to touch it:

```
root@fenrir:/# apt update
Hit:1 http://archive.ubuntu.com/ubuntu eoan InRelease
Get:2 http://archive.ubuntu.com/ubuntu eoan-updates InRelease [97.5 kB]
Get:3 http://archive.ubuntu.com/ubuntu eoan-backports InRelease [88.8 kB]
Get:4 http://archive.ubuntu.com/ubuntu eoan-security InRelease [97.5 kB]
Fetched 284 kB in 1s (341 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@fenrir:/# apt list --upgradable
Listing... Done
mailutils-common/eoan 1:3.6-1build1 all [upgradable from: 1:3.5-2build1]
mailutils/eoan 1:3.6-1build1 amd64 [upgradable from: 1:3.5-2build1]
root@fenrir:/# apt upgrade -y
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  mailutils mailutils-common
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-efi-amd64-signed (1.128.1+2.04-1ubuntu12.1) ...
Installing for x86_64-efi platform.
grub-install: warning: Cannot read EFI Boot* variables.
grub-install: warning: efivarfs_get_variable: read failed: Interrupted system call.
grub-install: warning: efi_get_variable: ops->get_variable failed: Interrupted system call.
grub-install: error: failed to register the EFI boot entry: Interrupted system call.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent processing triggers for shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have given up any hope to see the error in grub being fixed, or rather handled (issue is common on LGA1366 server boards, but these are getting a bit old), but I'd like to tell apt to ignore it.

How do I do that?

---

