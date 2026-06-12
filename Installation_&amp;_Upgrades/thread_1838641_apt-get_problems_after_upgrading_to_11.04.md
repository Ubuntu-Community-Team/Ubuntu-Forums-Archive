---
title: "apt-get problems after upgrading to 11.04"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by mpetrovic on 2011-09-04
While using 10.10 I've had 2.6.38-11 kernel. After upgrade to 11.04, linux image was "updated" to: "2.6.38.2-core2vgaswitch" (cannot boot at all to previous image) and since then any installation attempt fails at initramfs-update.

I've tried to force reinstall of udev and initramfs tools and still have the problems. Here's what's going on (any attempt to install anything ends like the one below for initramfs-tools):

```
milan@milan-ThinkPad-T510 ~ $ ls /var/cache/apt/archives/udev*
/var/cache/apt/archives/udev_162-2.2_amd64.deb
/var/cache/apt/archives/udev_167-0ubuntu3_amd64.deb

milan@milan-ThinkPad-T510 ~ $ sudo dpkg -i --force-all /var/cache/apt/archives/udev_167-0ubuntu3_amd64.deb
[sudo] password for milan: 
(Reading database ... 219676 files and directories currently installed.)
Preparing to replace udev 167-0ubuntu3 (using .../udev_167-0ubuntu3_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Setting up udev (167-0ubuntu3) ...
udev start/running, process 29478
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for man-db ...

milan@milan-ThinkPad-T510 ~ $ sudo apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
initramfs-tools is already the newest version.
The following packages were automatically installed and are no longer required:
  libqca2 libpolkit-qt-1-0 libjpeg8 libqca2-plugin-ossl libqt4-test
  libqt4-script libqt4-designer libqt4-network libqt4-core libqt4-opengl
  libqt4-gui libqt4-svg libfakekey0 freeglut3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-11-generic (2.6.38-11.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Warning: No support for locale: en_US.utf8
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    update-initramfs: Generating /boot/initrd.img-2.6.38.2-core2vgaswitch
Warning: No support for locale: en_US.utf8
cp: cannot stat `/usr/lib/pango/1.6.0/module-files.d/libpango1.0-0.modules': No such file or directory
cp: cannot stat `/usr/lib/pango/1.6.0/modules/pango-basic-fc.so': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.38.2-core2vgaswitch
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
milan@milan-ThinkPad-T510 ~ $ 
```

Any idea how to solve this?


edit:
if any install attempt is made through synaptic, it ends with the following additional error message in a popup:

E: linux-image-2.6.38-11-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: initramfs-tools: subprocess installed post-installation script returned error exit status 1

---

### Post by mörgæs on 2011-09-05
This happens way to often for online upgrades. I guess the fastest solution is a back up and a reinstall.

---

