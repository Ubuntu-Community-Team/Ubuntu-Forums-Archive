---
title: "You already have a NoLOADER configuration in /etc/grub.conf"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by GuiGuy on 2008-07-19
Using 8.04.

I've been getting the following error with apt-ugrade:

> 
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.34 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

[B]You already have a NoLOADER configuration in /etc/grub.conf
Running boot loader as requested
Running /usr/sbin/grub  ... 
Boot loader failed to run
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/B]


I assume the package 2.6.24-19.34 is never updated by 2.6.24-19.36, but I have no idea what, if anything, I should do to fix it. 

Is anyone able to help me sort this out?

Thanks

---

### Post by Pumalite on 2008-07-19
Try:
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by GuiGuy on 2008-07-19
> **Pumalite said:**
> Try:
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade

Thanks for the reply. apt-get clean terminates OK.

autoremove gives me:

> 

sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mcpp libcompizconfig0 libdebconfclient0 linux-headers-2.6.24-12-generic
  libdns32 linux-headers-2.6.24-12 libx11-xcb1 linux-headers-2.6.24-18
  linux-headers-2.6.24-18-generic liblaunchpad-integration0 libg2c0
  gcc-3.4-base
The following packages will be REMOVED:
  gcc-3.4-base libcompizconfig0 libdebconfclient0 libdns32 libg2c0
  liblaunchpad-integration0 libx11-xcb1 linux-headers-2.6.24-12
  linux-headers-2.6.24-12-generic linux-headers-2.6.24-18
  linux-headers-2.6.24-18-generic mcpp
0 upgraded, 0 newly installed, 12 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 138MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125626 files and directories currently installed.)
Removing libg2c0 ...
Removing gcc-3.4-base ...
Removing libcompizconfig0 ...
Removing libdebconfclient0 ...
Removing libdns32 ...
Removing liblaunchpad-integration0 ...
Removing libx11-xcb1 ...
Removing linux-headers-2.6.24-12-generic ...
Removing linux-headers-2.6.24-12 ...
Removing linux-headers-2.6.24-18-generic ...
Removing linux-headers-2.6.24-18 ...
Removing mcpp ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.34 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.34 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found kernel: /boot/vmlinuz-2.6.24-18-generic
Found kernel: /boot/vmlinuz-2.6.24-12-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

You already have a NoLOADER configuration in /etc/grub.conf
Running boot loader as requested
Running /usr/sbin/grub  ... 


I then have to do a CTRL C and get the same "Boot loader failed to run"  error 

Cheers

---

### Post by Pumalite on 2008-07-19
What script were you running when this happened?

---

### Post by GuiGuy on 2008-07-19
> **Pumalite said:**
> What script were you running when this happened?

I only sudo apt-get update then upgrade. I noticed it hung on 

> 
Updating /boot/grub/menu.lst ... done
You already have a NoLOADER configuration in /etc/grub.conf
Running boot loader as requested
Running /usr/sbin/grub ...


I waited for about 30 minutes then assumed it had gone pearshaped so CTRL + C'ed. At that point the error message is logged:

> 
Boot loader failed to run
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
linux-image-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Everything seems OK but it is evident the "Linux-image-2.6.24-19-nn" isn't being updated. 

Thanks

---

### Post by Pumalite on 2008-07-19
I don't have /etc/grub.conf in my Hardy.???

---

### Post by GuiGuy on 2008-07-20
> **Pumalite said:**
> I don't have /etc/grub.conf in my Hardy.???

Interesting. It exists only on our mythbuntu box (hardy). However, the others in our house, all ubuntu or kubuntu,  don't have it. 

Mind you, I have no idea what that means. :confused:

Cheers

---

