---
title: "upgrading kernel with manual GRUB"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by TheHimself on 2009-12-23
I have Ubuntu 9.04, Puppy and Moblin installed on my laptop (although I can't use the other two since wireless doesn't work ](*,)). Grub is in Puppy's partition and I got it by modifying Puppy's menu.lst. It works as a matter of fact and each time I upgrade Ubuntu's kernel I edit Grub manually.

However when upgrading ubuntu kernel I get error messages that grub can't be found and some stuff can't be configured.  How serious is this and can this be fixed? 
The following is what I got when reinstalling the latest version of kernrel.

```


Setting up linux-image-2.6.28-16-generic (2.6.28-16.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.28-17-generic (2.6.28-17.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-17-generic:
 linux-restricted-modules-2.6.28-17-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-17-generic; however:
  PackNo apport report written because the error message indicates its a followup error from a previous failure.
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          age linux-restricted-modules-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.17.22); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.17.22); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-16-generic
 linux-image-2.6.28-17-generic
 linux-restricted-modules-2.6.28-17-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-16-generic (2.6.28-16.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.28-17-generic (2.6.28-17.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.17.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-17-generic:
 linux-restricted-modules-2.6.28-17-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-17-generic; however:
  Package linux-restricted-modules-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-16-generic
 linux-image-2.6.28-17-generic
 linux-image-generic
 linux-generic
 linux-restricted-modules-2.6.28-17-generic
 linux-restricted-modules-generic

```

---

### Post by TheHimself on 2009-12-23
OK. I decided to install the GRUB by Ubuntu. This way I don't have to edit menu.lst every time ubuntu is upgraded. I did the following

```
sudo grub-install /dev/sda
```

and then reinstalled the latest kernel image. It asked if I wanted a menu.lst to be created which I accepted. Then added the lines for Moblin and Puppy from the Grub in Puppy's partition to the end of this menu.lst and changed the name of the Grub directory in Puppy to "disables-Grub". Now everything works fine.

---

