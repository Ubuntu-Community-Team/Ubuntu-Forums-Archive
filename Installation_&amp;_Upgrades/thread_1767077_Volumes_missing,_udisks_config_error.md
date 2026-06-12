---
title: "Volumes missing, udisks config error"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by Simbilis on 2011-05-25
After almost finishing the upgrade from 10.10 to 11.04, I hit a kernel  oops that interrupted the process. When I rebooted, I got a prompt  saying "[FONT=Courier New]The disk drive for /boot is not ready yet or present[/FONT]".  I opened the maintenance shell and dug around to find that a few  volumes, including the boot volume, didn't show up in /dev/mapper.  I  found and enabled them with 'vgscan --mknodes' but they were missing  again when I rebooted.

I booted with the 11.04 install CD,  installed mdadm and lvm2, and was able to assemble and mount all my  volumes including the formerly missing ones. I created a chroot  environment with all volumes mounted, successfully ran "update-initramfs  -u -k `uname-r`" (2.6.38-8-generic-pae), and rebooted, with the same  result.

I booted the install CD again, recreated the chroot environment, and tried running "dpkg --configure -a". I get this:

[FONT=Courier New]root@ubuntu:/# dpkg --configure -a
Setting up udisks (1.0.2-4ubuntu1) ...
udevadm trigger is not permitted while udev is unconfigured.
dpkg: error processing udisks (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lilo (1:22.8-10ubuntu1) ...
Running lilo...
Warning: LBA32 addressing assumed
Added Linux *
Added LinuxOLD
Warning: /dev/sdc is not on the first disk
The Master boot record of  /dev/sdc  has been updated.
The Master boot record of  /dev/sda  has been updated.
Warning: /dev/sdb is not on the first disk
The Master boot record of  /dev/sdb  has been updated.
3 warnings were issued.
dpkg: dependency problems prevent configuration of libgdu0:
 libgdu0 depends on udisks (>= 1.0.0); however:
  Package udisks is not configured yet.
 libgdu0 depends on udisks (<< 1.1.0); however:
  Package udisks is not configured yet.
dpkg: error processing libgdu0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs:
 gvfs depends on libgdu0 (>= 2.29.90); however:
  Package libgdu0 is not configured yet.
dpkg: error processing gvfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gvfs-backends:
 gvfs-backends depends on gvfs (= 1.8.0-0ubuntu2); however:
  Package gvfs is not configured yet.
dpkg: error processing gvfs-backends (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 udisks
 libgdu0
 gvfs
 gvfs-backends
[/FONT]
Any ideas on what to try next?

Thanks,

Sim

---

### Post by Simbilis on 2011-05-25
I was able to get the packages configured by commenting out the "udevadm trigger ..." in /var/lib/dpkg/info/udisks.postinst, but that hasn't fixed the problem of missing volumes at boot time.

---

### Post by Simbilis on 2011-05-25
Fixed by reinstalling udev.

---

### Post by TooMeeK on 2011-12-18
Thank You SOOO MUCH for this!!!
I just fixed ALL unconfigured packages with main problem with udev after switching from Ubuntu Server Lucid to Oneiric by simple reinstall udev!
There was another problem related to **info: unrecognized option '--convert-db'**
i just commented out lines 83-85 in **/var/lib/dpkg/info/udev.postinst** to workaround as described here: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/745011](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/745011)

---

