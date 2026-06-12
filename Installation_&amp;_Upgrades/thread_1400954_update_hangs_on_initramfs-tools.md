---
title: "update hangs on initramfs-tools"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by infox on 2010-02-07
This is a fresh install of the latest version of Ubuntu-Server under the latest version of vmware desktop, I have installed the ubuntu-desktop package and ran all updates which completed fine.  Upon trying trying to install then open vmware tools package the install hangs at this part: 

Running post-installation trigger initramfs-tools

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.31-19-server


It has been on this process for the last 3 hours and hasn't changed, the system is still operational at this point.  Any ideas on what might be the issue would be appreciated.

---

### Post by borneoo on 2010-05-02
Did you find some solution ?, Same for me: 10.04 64bit, desktop
....
Calling hook mdadm
Adding binary /sbin/mdadm
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/linear.ko
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/multipath.ko
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/raid0.ko
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/raid1.ko
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/raid456.ko
Adding module /lib/modules/2.6.32-14-generic/kernel/drivers/md/raid10.ko
Calling hook dmsetup
Building cpio /boot/initrd.img-2.6.32-14-generic.new initramfs
//the image is created ~10M

(a CTRL+C, cannot stop it)

thx

---

