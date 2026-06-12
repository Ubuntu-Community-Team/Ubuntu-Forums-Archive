---
title: "Video Issues, Kernel Crashes"
date: 2009-01-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yoman82 on 2009-01-25
As well suspected, the FGLRX drivers do not work in Jaunty. 
However, the Kernel fails to update, too, spitting out this error log whenever I use any package management. Help, please.
Setting up linux-image-2.6.28-4-generic (2.6.28-4.11) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-4-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.28-4-generic (--configure):
subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
linux-image-generic depends on linux-image-2.6.28-4-generic; however:
Package linux-image-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
dependency problems - leaving unconfigured
Setting up linux-image-2.6.27-11-generic (2.6.27-11.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.27-11.22 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.27-11.22 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (= 2.6.28.4.4); however:
Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-4-generic:
linux-restricted-modules-2.6.28-4-generic depends on linux-image-2.6.28-4-generic; however:
Package linux-image-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-4-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-4-generic; however:
Package linux-restricted-modules-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.4.4); however:
Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-image-2.6.28-4-generic
linux-image-generic
linux-image-2.6.27-11-generic
linux-generic
linux-restricted-modules-2.6.28-4-generic
linux-restricted-modules-generic
linux-restricted-modules

---

### Post by Slug71 on 2009-01-25
You should have Kernel 2.6.28-5??

---

### Post by yoman82 on 2009-01-25
The upgrade to 9.04 partially failed, it spit out that error message and could not upgrade the kernel. Everything else from the upgrade installed normally, though.

---

### Post by yoman82 on 2009-01-27
Bump

---

### Post by yoman82 on 2009-01-27
Bump

---

### Post by cariboo on 2009-01-27
Have you tried:

```
sudo apt-get install -f
```

You may have some missing dependencies that are needed to install the kernel.

JIm

---

### Post by yoman82 on 2009-01-29
sudo yoman82@Epic-80dlr-CPU:~$ sudo apt-get install -f
[sudo] password for yoman82: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 26 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27-11-generic (2.6.27-11.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.27-11.22 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.27-11.22 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-4-generic (2.6.28-4.11) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-4-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.28-4-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-5-generic (2.6.28-5.15) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-5-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/boot/grub/splashimages/earth-horizon.xpm.gz

expr: non-numeric argument
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error processing linux-image-2.6.28-5-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-4-generic:
 linux-restricted-modules-2.6.28-4-generic depends on linux-image-2.6.28-4-generic; however:
  Package linux-image-2.6.28-4-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-4-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-5-generic:
 linux-restricted-modules-2.6.28-5-generic depends on linux-image-2.6.28-5-generic; however:
  Package linux-image-2.6.28-5-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-5-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-5-genericNo apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                ; however:
  Package linux-image-2.6.28-5-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-5-generic; however:
  Package linux-restricted-modules-2.6.28-5-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.5.5); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.5.5); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules:
 linux-restricted-modules depends on linux-restricted-modules-generic (= 2.6.28.5.5); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-restricted-modules (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.27-11-generic
 linux-image-2.6.28-4-generic
 linux-image-2.6.28-5-generic
 linux-restricted-modules-2.6.28-4-generic
 linux-restricted-modules-2.6.28-5-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules
E: Sub-process /usr/bin/dpkg returned an error code (1)


Same error. I'm clueless.

---

### Post by yoman82 on 2009-01-31
This is quite serious, I need some help.

---

### Post by glasen on 2009-01-31
There is a very easy solution :

Deinstall every "linux-image-*"-package and after this reinstall the package "linux-generic" :

```
sudo apt-get remove --purge linux-image-2.6.27-11-generic linux-image-2.6.28-4-generic linux-image-2.6.28-5-generic

sudo apt-get install linux-generic
```

---

### Post by yoman82 on 2009-01-31
That didn't work, I still get the same errors.

---

### Post by marmuta on 2009-02-02
update-grub fails there. Can you install anything? Then try 
```
sudo apt-get install --reinstall grub

```
Else, what's the output of 
```
sudo update-grub

``` alone?

---

### Post by yoman82 on 2009-02-03
> **marmuta said:**
> update-grub fails there. Can you install anything? Then try 
```
sudo apt-get install --reinstall grub

```
Else, what's the output of 
```
sudo update-grub

``` alone?
Not working. It cites a "Non-numeric arugment"

---

### Post by Kow on 2009-02-03
Perhaps try moving /boot/grub/menu.lst to /boot/grub/menu.lst.bak and try running update-grub again. I get the feeling that your grub config is jacked. I also see that your splashimage is not the default so obviously you have messed with it at some point. Perhaps you can post your menu.lst and I may be able to find the problem. Looks like you are putting in a non-numeric value for a config setting that takes numbers only? Probably just a typo.

BTW, you may need to --reinstall grub as update-grub probably assumes a menu.lst already exists.

---

### Post by yoman82 on 2009-02-04
I gave up and reinstalled. Thanks anyway.

---

