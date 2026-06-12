---
title: "GRUB + LVM = GRUB _ at boot"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by darkphoenix16 on 2013-05-21
Hello everyone.

My hard drive has

/dev/sda1 (/boot)
/dev/sda2 (efi)
/dev/sda3 (lvm)
/dev/mapper/fedora-root (/)
/dev/mapper/fedora-home (/home)
/dev/mapper/fedora-win (unused atm)

I install using the ubuntu installation cd and when restarting I only get

GRUB _

on boot.  Left it for 10-20 minutes and there wasn't a change.  I had gentoo before and was able to get booting properly there.  I'm guessing that this is a lvm issue?

---

### Post by Herman on 2013-05-25
Probably you can make the new operating system bootable by chrooting into it and doing the following,
(a) add an /etc/crypttab file 
(b) edit /etc/initramfs-tools/modules
(c) create a new initrd.img

Useful links: 
 '[EncryptedFilesystemsViaUbiquity]("https://help.ubuntu.com/community/EncryptedFilesystemsViaUbiquity")' - Ubuntu Community Docs, 
'[Encrypted Filesystem LVM How-to]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")' - Ubuntu Community Docs, see especially this part: [final preparation]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto#Final_preparation"). 
' [how to chroot, simple and fast]("http://ubuntuforums.org/showthread.php?t=1156240")', by taavikko - Ubuntu Web Forums
[How to Resize a LUKS Encrypted File System]("http://ubuntuforums.org/showthread.php?p=4530641") - bodhi.zazen - Ubuntu Web Forums

---

