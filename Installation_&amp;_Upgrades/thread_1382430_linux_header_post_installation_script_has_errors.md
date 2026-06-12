---
title: "linux header post installation script has errors"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by mayankbhagya on 2010-01-15
When I updated to 2.6.31-16, I started getting these errors from the post installation scripts of linux-headers-2.6.31-16-generic and linux-image-2.6.31-16-generic.

Every time I used to install and remove any software, it gave me errors. Even the dpkg file shows these packages as half-configured packages.

I posted a thread on the forum and was told to comment out the erroneous lines in the /var/lib/dpkg/info/linux-image-2.6.31-16-generic.postinst & /var/lib/dpkg/info/linux-headers-2.6.31-16-generic.postinst script file.

Errors didn't appear for a while.
I then waited for the next kernel release and now even after upgrading to 2.6.31-17, I'm receiving similar errors!!

This is what happened when I tried to remove an older version of virtual box:

> $ sudo apt-get remove virtualbox-3.0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-3.0
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
5 not fully installed or removed.
After this operation, 86.9MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 193332 files and directories currently installed.)
Removing virtualbox-3.0 ...
 * Stopping VirtualBox kernel module                                             *  done.
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up linux-image-2.6.31-17-generic (2.6.31-17.54) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-17-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-17-generic
Found initrd image: /boot/initrd.img-2.6.31-17-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-17-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-17-generic; however:
  Package linux-image-2.6.31-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.17.30); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.31-17-generic (2.6.31-17.54) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                       Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-17-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-17-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-17-generic; however:
  Package linux-headers-2.6.31-17-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-2.6.31-17-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-17-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
$


Is there any permanent solution to this problem! Or atleast someone could tell me that what's wrong with my dpkg!

Help plzz!

---

### Post by mayankbhagya on 2010-01-20
Heelllllppppppp!!

---

