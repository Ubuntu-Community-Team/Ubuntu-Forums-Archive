---
title: "apt broken, how do i fix?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Polygon on 2009-03-27
so the updates that came through today contained some updates for linux-generic and all that, and it asked what i wanted to do to my menu.lst

through a mis understanding which i have now reported as a bug against debconf (here: [https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349666](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/349666)) i now have broken packages and i do not know how to fix them

if i run sudo apt-get -f install it just gives me this:

> 
mark@Polygon:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms patch
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.28-11-generic (2.6.28-11.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-11.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-11.37 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /vmlinuz-2.6.28-9-generic
Found kernel: /vmlinuz-2.6.27-14-generic
Found kernel: /vmlinuz-2.6.27-13-generic
Found kernel: /vmlinuz-2.6.27-12-generic
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-9-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Merging changes into the new version

 Conflicts found! Please edit `/var/run/grub/menu.lst' and sort them out manually.
 The file `/var/run/grub/menu.lst.ucf-new' has a record of the failed merge of the configuration file.

User postinst hook script [/sbin/update-grub] exited with value 3
dpkg: error processing linux-image-2.6.28-11-generic (--configure):
 subprocess post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-11-generic; however:
  Package linux-image-2.6.28-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.11.14); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.28-11-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


so....options?

---

