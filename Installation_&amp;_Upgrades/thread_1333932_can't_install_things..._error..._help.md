---
title: "can't install things... error... help?"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by sngehl01 on 2009-11-21
whenever i try to install something i get this error:

installArchives() failed: Selecting previously deselected package libsword8. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 148591 files and directories currently installed.) 
Unpacking libsword8 (from .../libsword8_1.6.0+dfsg-1_i386.deb) ... 
Selecting previously deselected package bibletime-data. 
Unpacking bibletime-data (from .../bibletime-data_2.0-1_all.deb) ... 
Selecting previously deselected package bibletime. 
Unpacking bibletime (from .../bibletime_2.0-1_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for menu ... 
Setting up linux-image-2.6.31-15-generic (2.6.31-15.50) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.31-15-generic 
Running postinst hook script /usr/sbin/update-grub. 
Generating grub.cfg ... 
No path or device is specified. 
Try ``grub-probe --help'' for more information. 
No path or device is specified. 
Try ``grub-probe --help'' for more information. 
User postinst hook script [/usr/sbin/update-grub] exited with value 1 
dpkg: error processing linux-image-2.6.31-15-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up grub-pc (1.97~beta4-1ubuntu4) ... 
Installation finished. No error reported. 
This is the contents of the device map /boot/grub/device.map. 
Check if this is correct or not. If any of the lines is incorrect, 
fix it and re-run the script `grub-install'. 
 
(hd0)    /dev/sda 
Generating grub.cfg ... 
No path or device is specified. 
Try ``grub-probe --help'' for more information. 
No path or device is specified. 
Try ``grub-probe --help'' for more information. 
dpkg: error processing grub-pc (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-2.6.31-15-generic; however: 
  Package linux-image-2.6.31-15-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 2.6.31.15.28); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up libsword8 (1.6.0+dfsg-1) ... 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
 
Setting up bibletime-data (2.0-1) ... 
Setting up bibletime (2.0-1) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 linux-image-2.6.31-15-generic 
 grub-pc 
 linux-image-generic 
 linux-generic 



any ideas why? i tried changing my grub boot menu background, and i may have porked something up bad.

---

### Post by sngehl01 on 2009-11-22
anyone??

---

### Post by dcottingham on 2009-11-22
Far as I can tell it looks like your updater has a kernel update somehow stuck in its craw. But it looks like the installation of that packages you asked for got done ok. It looks like it's just complaining that it can't complete the installation of the kernel update. Do I have this right -- you can still install other things ok?

---

### Post by sngehl01 on 2009-11-26
nope can't install things ok. i'll probably just reinstall ubuntu to my partition

---

