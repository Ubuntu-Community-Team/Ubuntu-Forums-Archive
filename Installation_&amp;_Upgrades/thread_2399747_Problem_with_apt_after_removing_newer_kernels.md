---
title: "Problem with apt after removing newer kernels"
date: 2018-08-29
forum: Installation &amp; Upgrades
---

### Post by kernelalive2 on 2018-08-29
Hello !
I have the  following problem : 
I use kernel headers 4.13.0-43-generic. I have installed as well linux-image-4.15.0-29-generic , linux-image-4.15.0-32-generic ,  linux-image-4.15.0-33-generic. Yesterday I tried to remove 4.15.* headers and got me tangled with the following error.
whenever I use apt command I receive 

> The following packages will be REMOVED:
  linux-image-4.15.0-29-generic linux-image-4.15.0-32-generic
  linux-image-4.15.0-33-generic
0 upgraded, 0 newly installed, 3 to remove and 16 not upgraded.
4 not fully installed or removed.
After this operation, 24,4 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 375333 files and directories currently installed.)
Removing linux-image-4.15.0-29-generic (4.15.0-29.31~16.04.1) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.13.0-43-generic.efi.signed
Failed to create or replace /vmlinuz: Is a directory at /usr/bin/linux-update-symlinks line 72.
dpkg: error processing package linux-image-4.15.0-29-generic (--remove):
 subprocess installed post-removal script returned error exit status 21
Removing linux-image-4.15.0-32-generic (4.15.0-32.35~16.04.1) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.13.0-45-generic
I: /initrd.img.old is now a symlink to boot/initrd.img-4.13.0-45-generic
Failed to create or replace /vmlinuz: Is a directory at /usr/bin/linux-update-symlinks line 72.
dpkg: error processing package linux-image-4.15.0-32-generic (--remove):
 subprocess installed post-removal script returned error exit status 21
Removing linux-image-4.15.0-33-generic (4.15.0-33.36~16.04.1) ...
I: /vmlinuz.old is now a symlink to boot/vmlinuz-4.13.0-43-generic.efi.signed
Failed to create or replace /vmlinuz: Is a directory at /usr/bin/linux-update-symlinks line 72.
dpkg: error processing package linux-image-4.15.0-33-generic (--remove):
 subprocess installed post-removal script returned error exit status 21
Errors were encountered while processing:
 linux-image-4.15.0-29-generic
 linux-image-4.15.0-32-generic
 linux-image-4.15.0-33-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have tried ```
 dpkg --configure -a 
``` but no luck. Any suggestions?? I am kinda stuck with this .
Thank you in advance .

---

### Post by kernelalive2 on 2018-08-29
I have managed to find the solution to my problem by purging every linux-image I didn t want.And after that I followed this 

   ```
  Code:
     / $ sudo mv initrd.img initrd.img\~
/ $ sudo mv vmlinuz vmlinuz\~
/ $ sudo ln -s boot/initrd.img-2.6.18-4-486 initrd.img-2.6.18-4-486
/ $ sudo ln -s boot/vmlinuz-2.6.18-4-486 vmlinuz-2.6.18-4-486
/ $ sudo /sbin/shutdown -r now 
Reboot was successful, no errors that I saw. I then upgraded some  program to trigger the apt-get error. I chose tzdata because it's small.

     Code:
     ~ $ sudo apt-get install tzdata
Setting up linux-image-2.6.18-4-486 (2.6.18.dfsg.1-12) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
Running postinst hook script /sbin/update-grub.
Your /etc/kernel-img.conf needs to be updated. Read grub's NEWS.Debian[1]
file and follow its instructions.

  1. /usr/share/doc/grub/NEWS.Debian.gz

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.18-4-486
Updating /boot/grub/menu.lst ... done

Press return to continue. 
[FONT=X-LocaleSpecific]
[/FONT]


```

CHEERS!!

---

