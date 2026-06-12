---
title: "UEFI boot repair pb"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by marcteyssier on 2013-02-14
I have a problem to repair my grub boot
[http://paste.ubuntu.com/1651460/](http://paste.ubuntu.com/1651460/)

---

### Post by oldfred on 2013-02-14
Welcome to the forums.

What model computer is this?

We have seen several systems with "locked" efi partitions. I do not even understand how on an efi partition they can prevent writing, but some systems do that.

Do you have secure boot off and fast boot off?

One solution is to totally backup the efi partition that has the Windows boot files (backup is a good idea anyway). delete the entire efi partition. then recreate it with gparted and add boot flag to make it the efi partition again, and copy Windows boot files back. Then you should be able to use Boot-Repair to install grub-efi or add grub's files to efi partition.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)
Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

---

