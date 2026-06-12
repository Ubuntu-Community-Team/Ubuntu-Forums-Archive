---
title: "grub bootloader failed to install"
date: 2016-12-29
forum: Installation &amp; Upgrades
---

### Post by cookieplz on 2016-12-29
Hi,


I am having some difficulties installing ubuntu 16.04 from a USB drive on a relatively new x1 carbon laptop. 

I get the error "the grub-efi-amd64-signed' package failed to install. Without the grub bootloader the system will not boot.

I ran the boot-info tool and created a paste bin here: [http://paste2.org/mOBF9473](http://paste2.org/mOBF9473)
any help would be appreciated.

---

### Post by oldfred on 2016-12-30
It looks like you have Secure boot on.
I would mount the encrypted partition when in Boot-Repair and run its fixes.
The UEFI install sets the ESP - efi system partition as hidden. Boot-Repair will change that from the 0077 to defaults so it can be updated.

We have seen some systems where the ESP is corrupted and needs dosfsck or even deletion & recreation.
       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

