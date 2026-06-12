---
title: "how to extend root partition with gparted"
date: 2018-02-09
forum: Installation &amp; Upgrades
---

### Post by vincent727 on 2018-02-09
My desktop pc is win10 / ubuntu 16.04 dual system.  Now I have an issue that the root space is almost full and cannot update and install softwares. Attached is my gparted report. After reviewing the instruction through the web it seems a little confusing to me. How to resize the root with gparted?

Seeking for help here.

---

### Post by jl2414 on 2018-02-09
Hello,

You can try to use these commands first to clean up a little:

Open Terminal and write or copy in and hit enter.

sudo apt autoclean

sudo apt autoremove

This to commands is for clean up old files.
You will be asked if you really want to delete these files.

I'm not a long time user but you can try these aforementioned.

Hope it help you a little bit until some more experienced are be able to help you.

Take care and good luck.

---

### Post by cruzer001 on 2018-02-09
Your root (/) partition is ok.  You have used 10.5G and have 8G unused.

Its your /boot that is too small.  I would think you have received warning messages about this.

And your swap partition does not need to be that large.

So since your swap and your /boot are next to each other I would take about 1.5G from swap and give it to /boot.

Other than that, your linux partitions look good.

Also be aware that there is always a risk involved when doing this.  It should go well, but it is never a sure thing.

---

### Post by Impavidus on 2018-02-09
Your root partition is fine. It's only slightly more than half full. Your /boot partition is the problem. But why do you have a /boot partition anyway? You only need it for LVM or full disk encryption, but you don't use that.

You can't modify a mounted partition and the partition with your running system is always mounted, so to modify partitions you have to run from a live disk. Right click in swap and set swap off if you want to modify the swap partition. Don't use gparted to modify Windows partitions; use Windows tools instead. But don't use Windows tools to modify Linux partitions.

---

### Post by vincent727 on 2018-02-09
> **jl2414 said:**
> Hello,

You can try to use these commands first to clean up a little:

Open Terminal and write or copy in and hit enter.

sudo apt autoclean

sudo apt autoremove

This to commands is for clean up old files.
You will be asked if you really want to delete these files.

I'm not a long time user but you can try these aforementioned.

Hope it help you a little bit until some more experienced are be able to help you.

Take care and good luck.


Thanks for your help!
After running the ```
sudo apt autoclean
``` && ```
sudo apt autoremove
```, I got the following outcome:


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-4.13.0-32-generic (4.13.0-32.35~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-32-generic /boot/vmlinuz-4.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-32-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-32-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-32-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-hwe-16.04:
 linux-image-generic-hwe-16.04 depends on linux-image-extra-4.13.0-32-generic; however:
  Package linux-image-extra-4.13.0-32-generic is not configured yet.


dpkg: error processing package linux-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.13.0.32.52); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.


dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-4.13.0-31-generic (4.13.0-31.34~16.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-31-generic /boot/vmlinuz-4.13.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-31-generic /boot/vmlinuz-4.13.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-31-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-31-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-signed-image-generic-hwe-16.04:
 linux-signed-image-generic-hwe-16.04 depends on linux-image-extra-4.13.0-32-generic; however:
  Package linux-image-extra-4.13.0-32-generic is not configured yet.


dpkg: error processing package linux-signed-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-signed-generic-hwe-16.04:
 linux-signed-generic-hwe-16.04 depends on linux-signed-image-generic-hwe-16.04 (= 4.13.0.32.52); however:
  Package linux-signed-image-generic-hwe-16.04 is not configured yet.


dpkg: error processing package linux-signed-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools (0.122ubuntu8.10) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-32-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-32-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.13.0-32-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-image-extra-4.13.0-31-generic
 linux-signed-image-generic-hwe-16.04
 linux-signed-generic-hwe-16.04
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have run into this same problem for many times. What should I do next?

---

### Post by yancek on 2018-02-09
Ubuntu site below explains in detail how to remove old kernels which you need to do.

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by vincent727 on 2018-02-09
> **cruzer001 said:**
> Your root (/) partition is ok.  You have used 10.5G and have 8G unused.

Its your /boot that is too small.  I would think you have received warning messages about this.

And your swap partition does not need to be that large.

So since your swap and your /boot are next to each other I would take about 1.5G from swap and give it to /boot.

Other than that, your linux partitions look good.

Also be aware that there is always a risk involved when doing this.  It should go well, but it is never a sure thing.

Hello,
Thanks for your help!
I am looking for a safe way to  take part of the swap space and give it to /boot.  I looked up in google and have not found a good instruction yet. Will keep searching...

Thanks!

---

