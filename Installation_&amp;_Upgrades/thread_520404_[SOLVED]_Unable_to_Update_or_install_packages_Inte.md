---
title: "[SOLVED] Unable to Update or install packages Internal Error: Could not find image
S"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by Spiffster on 2007-08-08
Hi all,

I am new to Ubuntu and have just installed Ubuntu 7.04 on my Dell laptop. However when i ran update manager today i got an error message and now I cannot update or install anything. When i run dpkg --configure -a i get the following errors:

spiff@spiff-laptop:~$ sudo dpkg --configure -a
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.20-16-generic)
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic


Have i managed to screw up my linux kernel somehow? I can't seem to get this fixed.  Of course I am completely new to Linux so if this is an extremely stupid post please forgive my ignorance. Any help would be greatly appreciated!

--Spiffster

---

### Post by ruibernardo on 2007-08-09
Try this:

```
 sudo apt-get install -f
```

This should end any package installation that wasn't complete.

---

### Post by Spiffster on 2007-08-09
Hi,

When i run "apt-get install -f" i get much the same error message as before:
spiff@spiff-laptop:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.20-16-generic)
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.20-16-generic:
 linux-restricted-modules-2.6.20-16-generic depends on linux-image-2.6.20-16-generic; however:
  Package linux-image-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.20-16-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.20-16-generic; however:
  Package linux-restricted-modules-2.6.20-16-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic; however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic; however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.20-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.20-16-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


Cheers,
Spiffster

---

### Post by ruibernardo on 2007-08-09
And what about this?

```
 sudo dpkg -C
```

---

### Post by Spiffster on 2007-08-09
That gave me the following message:

spiff@spiff-laptop:~$ sudo dpkg -C
Password:
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-restricted-modules-2.6.20-16-generic Non-free Linux 2.6.20 modules on x8
 linux-image-generic  Generic Linux kernel image
 linux-restricted-modules-generic Restricted Linux modules for generic kernels
 linux-generic        Complete Generic Linux kernel

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-2.6.20-16-generic Linux kernel image for version 2.6.20 on x86/x86


Thanks for helping, it is much appreciated!

-- Spiffster

---

### Post by ruibernardo on 2007-08-09
> **Spiffster said:**
> 
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 linux-image-2.6.20-16-generic Linux kernel image for version 2.6.20 on x86/x86


This message says what to do:

```
 sudo dpkg --configure   linux-image-2.6.20-16-generic
```

This should solve the problem. :)

Cheers

---

### Post by Spiffster on 2007-08-09
and trying to configure the package with the porblem gave me the following:

spiff@spiff-laptop:~$ sudo dpkg --configure linux-image-2.6.20-16-generic
Setting up linux-image-2.6.20-16-generic (2.6.20-16.29) ...
Internal Error: Could not find image (/boot/vmlinuz-2.6.20-16-generic)
dpkg: error processing linux-image-2.6.20-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.20-16-generic

--Spiffster

---

### Post by ruibernardo on 2007-08-09
Hmmm, try removing it completely and then reinstall again:

```
sudo dpkg -P linux-image-2.6.20-16-generic

sudo dpkg -i linux-image-2.6.20-16-generic
```

---

### Post by Spiffster on 2007-08-09
That yielded:

spiff@spiff-laptop:~$ sudo dpkg -P linux-image-2.6.20-16-generic
(Reading database ... 105883 files and directories currently installed.)
Removing linux-image-2.6.20-16-generic ...
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.20-16-generic ...
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.20-15-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: /lib/modules/2.6.20-16-generic: Directory not empty


spiff@spiff-laptop:~$ sudo dpkg -i linux-image-2.6.20-16-generic
dpkg: error processing linux-image-2.6.20-16-generic (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.20-16-generic

---

### Post by ruibernardo on 2007-08-09
Sorry, you got to go to /var/cache/apt/archives and do it there:

```
 cd /var/cache/apt/archives
sudo dpkg -i linux-image-2.6.20-16-generic
```

---

### Post by Spiffster on 2007-08-09
Result:
spiff@spiff-laptop:/var/cache/apt/archives$ sudo dpkg -i linux-image-2.6.20-generic
dpkg: error processing linux-image-2.6.20-generic (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.20-generic

When i list the contents of /var/cache/apt/archives i find the following files starting with linux:
linux-generic_2.6.20.16.28.1_i386.deb
linux-headers-2.6.20-16_2.6.20-16.29_i386.deb
linux-headers-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-headers-generic_2.6.20.16.28.1_i386.deb
linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
linux-image-generic_2.6.20.16.28.1_i386.deb
linux-restricted-modules-2.6.20-16-generic_2.6.20.5-16.29_i386.deb
linux-restricted-modules-common_2.6.20.5-16.29_all.deb
linux-restricted-modules-generic_2.6.20.16.28.1_i386.deb

Cheers,
--Spiffster

---

### Post by ruibernardo on 2007-08-09
It must be linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb

```
sudo dpkg -i linux-image-2.6.20-16-generic_2.6.20-16.29_i386.deb
```

---

### Post by Spiffster on 2007-08-09
Yes this seems to have done the trick.

Thank you so much for your help, it has been much appreciated! :)

--Spiffster

---

### Post by ruibernardo on 2007-08-09
Glad it worked. :D

---

