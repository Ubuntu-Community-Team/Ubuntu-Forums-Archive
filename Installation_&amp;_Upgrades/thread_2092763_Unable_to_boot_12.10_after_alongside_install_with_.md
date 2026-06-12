---
title: "Unable to boot 12.10 after alongside install with Windows 7"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by loopeando on 2012-12-08
Hello,

I'm trying to install 12.10 on an ASUS K55N.

I've downloaded Ubuntu 12.10 security remix, installed it alongside with Windows 7 Home Premium and after the install it went to Windows without prompting which OS to boot.

I've tried the steps described on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but they didn't work.

As instructed on the document here's the result I got from boot-repair [http://paste.ubuntu.com/1419769/](http://paste.ubuntu.com/1419769/)

Can anyone help?

Thanks in advance.

---

### Post by darkod on 2012-12-08
It looks like you didn't boot the cd in uefi mode. Ubuntu was installed in legacy mode.

You need to boot the cd in uefi mode so that ubuntu installs in uefi mode too. In the first link you posted, read more carefully the section that says: Identifying if the computer boots the CD in EFI mode.

---

### Post by oldfred on 2012-12-09
Boot-Repair can also convert a BIOS install to UEFI install by uninstalling grub-pc and installing grub-efi. But it looks like you ran it from the BIOS mode install. You have to boot Ubuntu in UEFI mode for either reinstalling or repairing.

---

