---
title: "[lubuntu] Installing with disk encryption (LUKS) on XenServer"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by stone circle on 2015-10-13
Hi,

Has anyone managed to install Lubuntu (14.04.3) in Xenserver with disk encryption?  I initially got an "unsafe swap file" error in the install GUI, which is a known issue - [workaround is to install using the "Alternate" boot image]("http://askubuntu.com/questions/393418/unsafe-swap-space-detected"), which seemed to then install fine.  However, during boot, the VM fails to prompt for the LUKS decrypt password, and just freezes on the Citrix POST screen below.
[IMG]http://brendanh.com/13-10-2015210239.png[/IMG]

I'm ticking the *Encrypt the whole Lubuntu installation* and* Use LVM* boxes.  I expect some Grub gymnastics are necessary because the normal /dev/sda# file system is replaced by /dev/xvda# notation in XenServer.  Ubuntu 14.04 installs fine on an encrypted disk in Xen, so I doubt it'll take much engineering to get Lubuntu working likewise.  

I've tried booting from the Lubuntu Live ISO, choosing "Rescue a broken system" and "Install the GRUB boot loader" to no avail.  Through the same means I can mount the encrypted file system (device: /dev/<VM NAME>-vg/root), but I'm no grub expert. Is there a log that'll help me gain more info? dmesg isn't written to.   The /boot file system is /dev/xvda1 which is flagged bootable in fdisk.

Many thanks

---

### Post by stone circle on 2015-10-14
Ignore this, installed Lubuntu second time with disk encryption and it booted fine.  Don't know where I went wrong the first time.

---

