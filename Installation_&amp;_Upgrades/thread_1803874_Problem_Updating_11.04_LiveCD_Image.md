---
title: "Problem Updating 11.04 LiveCD Image"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by Slim Backwater on 2011-07-14
I'm following the instructions from here:

[https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization")

Everything has gone well, and I'm into the chroot environment.

I have completed an apt-get update && apt-get upgrade and I'm stuck on apt-get dist-upgrade to get the kernel updates.

It seems I have a problem with grub that's preventing the kernel from configuring.  The LiveCD doesn't even use grub so I'm not sure what to do.

```

root@ubuntu:/# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
/usr/sbin/grub-probe: error: cannot stat `/media/008484C88484C1A0/Work/temp'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                           Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I think it hinges on ```
/usr/sbin/grub-probe: error: cannot stat `/media/008484C88484C1A0
```

/media/008484C88484C1A0 is an NTFS volume where I've created a 4-GB file holding an ext3 filesystem to hold the unsquashfs. (I've booted off the USB I'm hoping to update)

Thanks for any help.

*Edit: I did an ```
apt-get purge grub-pc
``` and the update succeeded.

---

