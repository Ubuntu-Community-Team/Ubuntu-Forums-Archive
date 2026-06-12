---
title: "lastest upgrade didn't complete"
date: 2018-11-24
forum: Installation &amp; Upgrades
---

### Post by jfaberna on 2018-11-24
I got an upgrade notice and run it last night. It failed for some reason.  The  message about no room left on device can't be right.
/dev/sda1                     523248      6228     517020              2% /boot/efi
/dev/sdb1                  479669932  82424924  372809348  19% /home
/dev/sda3                   60394012   8023836   49272544     15% /

Console output is below:

```

Setting up grub-efi-amd64-signed (1.93.10+2.02-2ubuntu8.9) ...
Installing for x86_64-efi platform.
** Warning ** : Boot000a is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000b is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000c is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000d is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000a is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000b is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000c is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000d is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000a is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000b is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000c is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : Boot000d is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
Could not prepare Boot variable: No space left on device
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-efi-amd64-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any ideas?

---

### Post by jfaberna on 2018-11-24
I tried boot-repair and it didn't fix it but gave this output.

[http://paste.ubuntu.com/p/2gZZNpTPYr/](http://paste.ubuntu.com/p/2gZZNpTPYr/)

---

### Post by jfaberna on 2018-11-27
I just received some updates this morning and the problem with the last upgrade got fixed and now I'm back to normal

---

