---
title: "How to change partition labels on exfat partition"
date: 2022-08-25
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-08-25
How do I change /media/john/FB17-F816 (/dev/sda13) to /media/john/MyDocuments and have the Label read MyDocuments?

Thank you,

john

---

### Post by ActionParsnip on 2022-08-25
You can use GParted to label stuff if GUI is your style. The file system will need to be unmounted to be manipulated

---

### Post by cigtoxdoc on 2022-08-25
Thank you.  The first time I tried this with a bootable Gparted USB, it did not work.  However, I don't have the correct FSTAB in place, so the partition in question doesn't mount.  So I could use Gparted from a normal boot and it did work.  John

---

### Post by ActionParsnip on 2022-08-25
You can use gparted in a booted OS. Just unmount the file system, name it and then remount. You can add file systems to fstab using UUID

---

