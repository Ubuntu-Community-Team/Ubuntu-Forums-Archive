---
title: "Live CD: Can not mount /dev/loop0...on //filesystem.squashfs"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by outofnicks on 2011-03-14
xubuntu iso was downloaded with wget on Kubuntu, I did a md5sum checksum in terminal which passed, also K3b's check passed. K3b burned iso with no errors, I set speed at 4x. I made two coasters before getting this far but it still won't get past the BusyBox built-in shell prompt after choosing my language and staring at the xfce mouse for a minute:
```
BusyBox v15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```
is what I get when trying to boot live cd on both my Linux PC and Windows XP box.

Where can I go next please?

---

### Post by outofnicks on 2011-03-16
After doing a search for "Can not mount /dev/loop0" I found a few threads with the same issue, fairly common on which has been a bit of a thorn in the side of Ubuntu.
The only way I could get around it was using the mini.iso Minimal Install and doing a net install.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

