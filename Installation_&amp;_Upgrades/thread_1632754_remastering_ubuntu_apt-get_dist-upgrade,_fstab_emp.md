---
title: "remastering ubuntu: apt-get dist-upgrade, fstab empty, initrd.img does not update"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by Faustux on 2010-11-28
System: Ubuntu 10.10 i386 CD

I followed the instructions at [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization). But I cannot upgrade the livecd using:
# apt-get update
# apt-get dist-upgrade --install-recommends

it was not possible with aptitude as well

here's the output of the commands that I issued at the chrooted filesystem:
```

faust@faust:/# sudo apt-get -u dist-upgrade --install-recommends
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cups
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-22-generic (2.6.35-22.35) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
cryptsetup: WARNING: could not determine root device from /etc/fstab
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-22-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
cryptsetup: WARNING: could not determine root device from /etc/fstab
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                           dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-23-generic; however:
  Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Please tell me what's wrong.
Thanks in advance.
---
LPIC-2 Senior Linux Administrator
Novell Certified Data Center Technical Specialist
Novell Certified Suse Enterprise 11 Administrator

---

### Post by prabs on 2010-11-28
me too on the same lane of remastering but iam using the Reconstructor tool for customizing  and also you can use [www.susestudio.com](www.susestudio.com) for building you own LINUX distro !!!!

---

