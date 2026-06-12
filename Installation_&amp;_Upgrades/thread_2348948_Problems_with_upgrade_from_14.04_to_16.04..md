---
title: "Problems with upgrade from 14.04 to 16.04."
date: 2017-01-09
forum: Installation &amp; Upgrades
---

### Post by Mista G Nerd on 2017-01-09
Recently I upgraded my brothers old hardware and decided to upgrade his software as well. I do this for him every few years (last time was from 12.04 to 14.04).

I updated 14.04, then upgraded to 16.04. Upon completion I received some errors with old kernel packages and an initramfs error upon login. Yet, i'm at a loss as to how to proceed. So here's what I get returned.

sudo apt-get update
```
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [190 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:10 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:12 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:13 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.2 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19.5 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 1,225 kB in 2s (597 kB/s)   
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
```

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-93-generic
The following packages have been kept back:
  libpurple-bin
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
8 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 446039 files and directories currently installed.)
Removing linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
WARNING: missing /lib/modules/3.13.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Eatkcb/lib/modules/3.13.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Eatkcb/lib/modules/3.13.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Fatal: open /boot/vmlinuz-3.13.0-93-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

uname -r
```
4.4.0-57-generic
```

ls -l /boot
```
total 272736
-rw-r--r-- 1 root root  1166834 Dec  6 11:22 abi-3.13.0-106-generic
-rw-r--r-- 1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r-- 1 root root  1161764 Jun  4  2014 abi-3.13.0-29-generic
-rw-r--r-- 1 root root  1162712 Jul 14  2014 abi-3.13.0-32-generic
-rw-r--r-- 1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r-- 1 root root  1243800 Dec  9 22:04 abi-4.4.0-57-generic
-rw-r--r-- 1 root root      512 Jan  8 14:11 boot.0800
-rw-r--r-- 1 root root      512 Aug 19 22:19 boot.0810
-rw-r--r-- 1 root root      512 Aug 19 22:19 boot.0820
-rw-r--r-- 1 root root   113162 Jan  8 18:46 coffee.bmp
-rw-r--r-- 1 root root   166061 Dec  6 11:22 config-3.13.0-106-generic
-rw-r--r-- 1 root root   165510 May  2  2014 config-3.13.0-24-generic
-rw-r--r-- 1 root root   165544 Jun  4  2014 config-3.13.0-29-generic
-rw-r--r-- 1 root root   165611 Jul 14  2014 config-3.13.0-32-generic
-rw-r--r-- 1 root root   165611 Aug 13  2014 config-3.13.0-34-generic
-rw-r--r-- 1 root root   189991 Dec  9 22:04 config-4.4.0-57-generic
-rw-r--r-- 1 root root    22466 Jan  8 18:46 debian.bmp
-rw-r--r-- 1 root root    22560 Jan  8 18:46 debian-de.bmp
-rw-r--r-- 1 root root    31628 Jan  8 18:46 debianlilo.bmp
drwxr-xr-x 5 root root     4096 Jan  8 19:19 grub
-rw-r--r-- 1 root root 31561136 Jan  8 17:56 initrd.img-3.13.0-106-generic
-rw-r--r-- 1 root root 19283005 Jan  8 16:54 initrd.img-3.13.0-106-generic.dpkg-bak
-rw-r--r-- 1 root root 19118785 Jan  8 14:14 initrd.img-3.13.0-24-generic
-rw-r--r-- 1 root root 19124435 Jan  8 14:13 initrd.img-3.13.0-29-generic
-rw-r--r-- 1 root root 19180417 Jan  8 14:12 initrd.img-3.13.0-32-generic
-rw-r--r-- 1 root root 19181265 Jan  8 14:12 initrd.img-3.13.0-34-generic
-rw-r--r-- 1 root root  9542563 Jan  9 13:55 initrd.img-3.13.0-93-generic
-rw-r--r-- 1 root root 37960579 Jan  8 19:11 initrd.img-4.4.0-57-generic
-rw-r--r-- 1 root root 37960744 Jan  8 18:47 initrd.img-4.4.0-57-generic.dpkg-bak
-rw-r--r-- 1 root root    22578 Jan  8 18:46 inside.bmp
-rw------- 1 root root   512000 Jan  8 14:23 map
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r-- 1 root root     6878 Jan  8 18:46 onlyblue.bmp
-rw------- 1 root root  3399674 Dec  6 11:22 System.map-3.13.0-106-generic
-rw------- 1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw------- 1 root root  3378267 Jun  4  2014 System.map-3.13.0-29-generic
-rw------- 1 root root  3381262 Jul 14  2014 System.map-3.13.0-32-generic
-rw------- 1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic
-rw------- 1 root root  3875329 Dec  9 22:04 System.map-4.4.0-57-generic
-rw-r--r-- 1 root root    33192 Jan  8 18:46 tuxlogo.bmp
-rw------- 1 root root  5849616 Dec  6 11:22 vmlinuz-3.13.0-106-generic
-rw------- 1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic
-rw------- 1 root root  5792544 Jun  4  2014 vmlinuz-3.13.0-29-generic
-rw------- 1 root root  5798112 Jul 14  2014 vmlinuz-3.13.0-32-generic
-rw------- 1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw------- 1 root root  7067152 Dec  9 22:04 vmlinuz-4.4.0-57-generic
```

dpkg -l | grep linux-image
```
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                   4.4.0.57.60                                   amd64        Generic Linux kernel image

```


it appears to me that linux-image-3.13.0-93-generic was completely removed however linux-image-extra-3.13.0-93-generic was partially uninstalled and is now causing my grief. The problem is no matter how hard I try I can't seem to remove it. Any thoughts or ideas?

---

### Post by Bashing-om on 2017-01-09
Mista G Nerd; Hello;

Yeah. looks like the culprit here is the -93 kernel .
Let's try - even without the supporting confirmation of existence :
```

sudo dpkg -P linux-headers-3.13.0-93-generic
sudo dpkg -P linux-headers-3.19.0-68
sudo dpkg -P linux-image-3.13.0-93-generic
sudo dpkg -P linux-image-extra-3.13.0-93-generic

```

Now if these run with no errors , let's next see if the package manager will perform it's thing :
```

sudo apt update
sudp apt upgrade
sudo apt autoremove

```
We want to get down to only 2 installed kernels.

And if these run clean, we want to know if we need to devote some additional efforts to clean up :
what shows:
```

df -h
df -i

```

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-09
Ran clean until trying to purge linux-image-extra-3.13.0-93-generic

sudo dpkg -P linux-headers-3.13.0-93-generic
```
dpkg: warning: ignoring request to remove linux-headers-3.13.0-93-generic which isn't installed
```

sudo dpkg -P linux-headers-3.19.0-68
```
dpkg: warning: ignoring request to remove linux-headers-3.19.0-68 which isn't installed
```

sudo dpkg -P linux-image-3.13.0-93-generic
```
dpkg: warning: ignoring request to remove linux-image-3.13.0-93-generic which isn't installed
```

sudo dpkg -P linux-image-extra-3.13.0-93-generic
```
(Reading database ... 446039 files and directories currently installed.)
Removing linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
WARNING: missing /lib/modules/3.13.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_T3ds2N/lib/modules/3.13.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_T3ds2N/lib/modules/3.13.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Fatal: open /boot/vmlinuz-3.13.0-93-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-93-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-93-generic
```

---

### Post by Bashing-om on 2017-01-09
Mista G Nerd; Yuk !

OK let's dig a bit deeper, and prepare to get dirty .
Show :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
see here how bad we might break the package manager ( or in this case how bad it is broken) .

We find a way
[INDENT]to move forward
[/INDENT]

---

### Post by Mista G Nerd on 2017-01-09
Somehow I thought these might return longer lists. 

ls -al /usr/src/
```
total 56
drwxr-xr-x 14 root root 4096 Jan  8 19:18 .
drwxr-xr-x 11 root root 4096 Jan  8 17:04 ..
drwxr-xr-x 24 root root 4096 Jan  8 14:21 linux-headers-3.13.0-106
drwxr-xr-x  7 root root 4096 Jan  8 14:21 linux-headers-3.13.0-106-generic
drwxr-xr-x 24 root root 4096 Jun 16  2014 linux-headers-3.13.0-24
drwxr-xr-x  7 root root 4096 Jun 16  2014 linux-headers-3.13.0-24-generic
drwxr-xr-x 24 root root 4096 Jun 16  2014 linux-headers-3.13.0-29
drwxr-xr-x  7 root root 4096 Jun 16  2014 linux-headers-3.13.0-29-generic
drwxr-xr-x 24 root root 4096 Aug  6  2014 linux-headers-3.13.0-32
drwxr-xr-x  7 root root 4096 Aug  6  2014 linux-headers-3.13.0-32-generic
drwxr-xr-x 24 root root 4096 Aug 19  2014 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 19  2014 linux-headers-3.13.0-34-generic
drwxr-xr-x 27 root root 4096 Jan  8 17:32 linux-headers-4.4.0-57
drwxr-xr-x  7 root root 4096 Jan  8 17:32 linux-headers-4.4.0-57-generic

```

ls -al /lib/modules/
```
total 32
drwxr-xr-x  8 root root 4096 Jan  8 19:19 .
drwxr-xr-x 25 root root 4096 Jan  8 17:20 ..
drwxr-xr-x  5 root root 4096 Jan  8 14:22 3.13.0-106-generic
drwxr-xr-x  5 root root 4096 Jun 16  2014 3.13.0-24-generic
drwxr-xr-x  5 root root 4096 Jun 16  2014 3.13.0-29-generic
drwxr-xr-x  5 root root 4096 Aug  6  2014 3.13.0-32-generic
drwxr-xr-x  5 root root 4096 Aug 19  2014 3.13.0-34-generic
drwxr-xr-x  5 root root 4096 Jan  8 18:47 4.4.0-57-generic
```

ls -al /boot/
```
total 272744
drwxr-xr-x  3 root root     4096 Jan  9 17:01 .
drwxr-xr-x 24 root root     4096 Jan  8 17:56 ..
-rw-r--r--  1 root root  1166834 Dec  6 11:22 abi-3.13.0-106-generic
-rw-r--r--  1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1161764 Jun  4  2014 abi-3.13.0-29-generic
-rw-r--r--  1 root root  1162712 Jul 14  2014 abi-3.13.0-32-generic
-rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1243800 Dec  9 22:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root      512 Jan  8 14:11 boot.0800
-rw-r--r--  1 root root      512 Aug 19 22:19 boot.0810
-rw-r--r--  1 root root      512 Aug 19 22:19 boot.0820
-rw-r--r--  1 root root   113162 Jan  8 18:46 coffee.bmp
-rw-r--r--  1 root root   166061 Dec  6 11:22 config-3.13.0-106-generic
-rw-r--r--  1 root root   165510 May  2  2014 config-3.13.0-24-generic
-rw-r--r--  1 root root   165544 Jun  4  2014 config-3.13.0-29-generic
-rw-r--r--  1 root root   165611 Jul 14  2014 config-3.13.0-32-generic
-rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic
-rw-r--r--  1 root root   189991 Dec  9 22:04 config-4.4.0-57-generic
-rw-r--r--  1 root root    22466 Jan  8 18:46 debian.bmp
-rw-r--r--  1 root root    22560 Jan  8 18:46 debian-de.bmp
-rw-r--r--  1 root root    31628 Jan  8 18:46 debianlilo.bmp
drwxr-xr-x  5 root root     4096 Jan  8 19:19 grub
-rw-r--r--  1 root root 31561136 Jan  8 17:56 initrd.img-3.13.0-106-generic
-rw-r--r--  1 root root 19283005 Jan  8 16:54 initrd.img-3.13.0-106-generic.dpkg-bak
-rw-r--r--  1 root root 19118785 Jan  8 14:14 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 19124435 Jan  8 14:13 initrd.img-3.13.0-29-generic
-rw-r--r--  1 root root 19180417 Jan  8 14:12 initrd.img-3.13.0-32-generic
-rw-r--r--  1 root root 19181265 Jan  8 14:12 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root  9542562 Jan  9 17:01 initrd.img-3.13.0-93-generic
-rw-r--r--  1 root root 37960579 Jan  8 19:11 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 37960744 Jan  8 18:47 initrd.img-4.4.0-57-generic.dpkg-bak
-rw-r--r--  1 root root    22578 Jan  8 18:46 inside.bmp
-rw-------  1 root root   512000 Jan  8 14:23 map
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root     6878 Jan  8 18:46 onlyblue.bmp
-rw-------  1 root root  3399674 Dec  6 11:22 System.map-3.13.0-106-generic
-rw-------  1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  3378267 Jun  4  2014 System.map-3.13.0-29-generic
-rw-------  1 root root  3381262 Jul 14  2014 System.map-3.13.0-32-generic
-rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic
-rw-------  1 root root  3875329 Dec  9 22:04 System.map-4.4.0-57-generic
-rw-r--r--  1 root root    33192 Jan  8 18:46 tuxlogo.bmp
-rw-------  1 root root  5849616 Dec  6 11:22 vmlinuz-3.13.0-106-generic
-rw-------  1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5792544 Jun  4  2014 vmlinuz-3.13.0-29-generic
-rw-------  1 root root  5798112 Jul 14  2014 vmlinuz-3.13.0-32-generic
-rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  7067152 Dec  9 22:04 vmlinuz-4.4.0-57-generic
```

dpkg -l | grep linux-
```
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
iF  linux-firmware                                        1.157.6                                       all          Firmware for Linux kernel drivers
iU  linux-generic                                         4.4.0.57.60                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-106                              3.13.0-106.153                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-106-generic                      3.13.0-106.153                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                                4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                        4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.57.60                                   amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
pH  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                   4.4.0.57.60                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-57.78                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2017-01-09
Mista G Nerd; OK ....

Let's hold off on my dirty notion and try a cleaner approach:
```

sudo apt -f install
sudo dpkg -C

```
As, it seems all that is left on the system for -93 kernel is  a .img and bits and pieces of linux-image-extra.
Maybe the -f (fix broken) will give us a better alternative to work to .

I would like to stay clean if at all possible.

[INDENT][INDENT]do the best we can with what we have to work with
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-09
Returns more of the same

sudo apt -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-93-generic
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
8 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 446039 files and directories currently installed.)
Removing linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
WARNING: missing /lib/modules/3.13.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PuApu6/lib/modules/3.13.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PuApu6/lib/modules/3.13.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Fatal: open /boot/vmlinuz-3.13.0-93-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

sudo dpkg -C
```
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 linux-generic        Complete Generic Linux kernel and headers
 linux-image-extra-4.4.0-57-generic Linux kernel extra modules for version 4.4.
 linux-image-generic  Generic Linux kernel image

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 initramfs-tools      generic modular initramfs generator (automation)
 lilo                 LInux LOader - the classic OS boot loader
 linux-firmware       Firmware for Linux kernel drivers
 linux-image-4.4.0-57-generic Linux kernel image for version 4.4.0 on 64 bit x8

The following packages are only half installed, due to problems during
installation.  The installation can probably be completed by retrying it;
the packages can be removed using dselect or dpkg --remove:
 linux-image-extra-3.13.0-93-generic Linux kernel extra modules for version 3.1
```

---

### Post by Bashing-om on 2017-01-09
Mista G Nerd; Yeah ...

That do give us direction .

Ouch though !

I do think the place to start from is the lilo install problems . However, I do not remember enough of that old boot loader to know now what to do . 
Let's sit and wait and see if others here can come to the rescue . Is there a particular reason that your Boot Loader is lilo rather than grub2 ??

[INDENT][INDENT]sometimes I just do not recall
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-09
@Bashing-om
Honestly I don't remember specifically why I chose lilo. As I said earlier this install has been carried over since I believe 11.04 when they first introduced Unity. I have since upgraded from 11.04 -> 12.04 -> 14.04 and now 16.04. The hardware has also changed, perhaps it was a hardware limitation at the time. I don't recall.

However, If I could change it without wiping that would be great. As I recently purchased a Win 10 OEM key from Kinguin.net, and would like to install it on this system alongside Ubuntu.

---

### Post by Bashing-om on 2017-01-09
Mista G Nerd; Welp ....

As I say I do not recall lilo - I do not know what will result if we were to install grub2 .
Best to wait for wiser heads here rather than bungle things up more .

If we get no guidance in some appropriate amount of time . I do the homework and see what it will take .

I have yet to break other's systems,
[INDENT][INDENT]I do not want that yours be the first .
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-01-10
Mista G Nerd; OK;

I think I have a handle on this . I still "think" our better approach here is to replace lilo with grub2; and then tackle the kernel issues .
Let's make sure of what we are working with and where we are to install the new boot loader to.
show:
```

sudo fdisk -lu

```

and away we go.

[INDENT][INDENT]we can do this ?
[/INDENT][/INDENT]

---

### Post by ubfan1 on 2017-01-10
I have found that if the package manager complains about missing files it is trying to remove, I just make the missing file  (sudo touch file) and the zero length file then lets the package manager avoid the failure.  Try that.

---

### Post by gobstopper2 on 2017-01-10
I'm having the same exact problem(found this thread after searching online), except I have the grub2 bootloader. Will keep checking this thread to see if the eventual solution works for me as well.

---

### Post by Mista G Nerd on 2017-01-11
sudo fdisk -lu```

Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x000478ff

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1  *         2048  400510975  400508928   191G 83 Linux
/dev/sda2       400510976 1953523711 1553012736 740.5G  5 Extended
/dev/sda5       400513024 1953523711 1553010688 740.5G  7 HPFS/NTFS/exFAT
```


Why does it show the same partition twice? Once as /dev/sda2 Extended and again as /dev/sda5 HPFS/NTFS/EXFAT. They have essentially the same start and end.


I'm not sure but i'm guessing I need to run these commands?

sudo mount --bind /dev /mnt/dev &&
sudo mount --bind /dev/pts /mnt/dev/pts &&
sudo mount --bind /proc /mnt/proc &&
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sda
grub-install --recheck /dev/sda
update-grub
exit &&
sudo umount /mnt/sys &&
sudo umount /mnt/proc &&
sudo umount /mnt/dev/pts &&
sudo umount /mnt/dev &&
sudo umount /mnt

> **ubfan1 said:**
> I have found that if the package manager  complains about missing files it is trying to remove, I just make the  missing file  (sudo touch file) and the zero length file then lets the  package manager avoid the failure.  Try that.

I'm afraid to do this because if you read the returned text. Is says that it couldn't load the file, and the following shows that its executing another file of the same kernel. So i feel (may be completely wrong) that to uninstall, the content of those files are needed other wise it's would do a simple check if the file exists rather than an attempt to load the file.

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Here we go.

Addressing your concerns 1st:
> 
Why does it show the same partition twice?

It is not, Your partitions are valid.
Let me explain.
In the MBR partitioning scheme there can only be 4 primary partitions - due to the ability to address in the boot sector. What we do to get around this addressing limitation is create an " extended " partition as one of the primary partitions ( here yours is sda2 - extended ) this extended partition is a container to hold addition "logical" partitions where there can be 128 additional partitions . Now in this container in your case is sda5 ( the 1st logical partition is always sda5 ) .

Now back to the situation at hand . As you are able to boot . we keep this at a simpler level; we have no present need to set up a CHange Root to effect the install of grub2 .
Now as to why install grub over lilo . I bet lilo has been broken for some time ! .. Lilo does not have the ability of grub to update when a new kernel is installed. With lilo and a new kernel one has to re-install and/or fix lilo .

Let's now install grub ;
```

sudo mkdir /boot/grub
sudo apt install grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub

```

Here I can accept that grub screams and hollers about the -93 kernel . IF it does we now need to address this;  Before rebooting !
Post all the commands and the outputs so I know what the target of our efforts are to be. I do want to keep this as clean as possible. Try not to make the package manager unhappier than it is .

Once we have the system booting from grub we will remove lilo .

still ;
[INDENT][INDENT]small steps
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-11
sudo mkdir /boot/grub
```
mkdir: cannot create directory ‘/boot/grub’: File exists
```

that's strange but i'll just roll with it.

sudo apt install grub-pc grub-common
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
grub-common is already the newest version (2.02~beta2-36ubuntu3.6).
grub-pc is already the newest version (2.02~beta2-36ubuntu3.6).
The following packages will be REMOVED:
  linux-image-extra-3.13.0-93-generic
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
8 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 446039 files and directories currently installed.)
Removing linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
WARNING: missing /lib/modules/3.13.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_eJ9KVn/lib/modules/3.13.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_eJ9KVn/lib/modules/3.13.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Fatal: open /boot/vmlinuz-3.13.0-93-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

again strange because I know I have lilo, yet grub is still showing...and i'm just gonna ignore the errors from trying to uninstall -93.

sudo grub-install /dev/sda
```
Installing for i386-pc platform.
Installation finished. No error reported.
```

Although my chip is intel, I have 64-bit. will this cause problems later?

sudo update-grub
```
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-106-generic
Found initrd image: /boot/initrd.img-3.13.0-106-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; looks good;

Regret my delay in responding - had to run to town .

Lilo and grub will co-exist but only one is in the boot sector to control booting . In our case grub, now .
We will remove lilo at a later time.

I do think that grub will be and is happy . But the -93 kernel still bothers me . I do want it cleaned up before we proceed .
Show me a new :
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

``` to make sure the system has not done anything that I am unprepared for.
As:
> 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic

lilo is still calling for the -93 kernel !

bk

> 
Although my chip is intel, I have 64-bit. will this cause problems later?

Nope, we are in good shape here . AMD has the rights to 64 bit processing so they retain the "name" no matter the architecture .

[INDENT][INDENT]I do like clean
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-11
ls -al /usr/src/
```
total 56
drwxr-xr-x 14 root root 4096 Jan  8 19:18 .
drwxr-xr-x 11 root root 4096 Jan  8 17:04 ..
drwxr-xr-x 24 root root 4096 Jan  8 14:21 linux-headers-3.13.0-106
drwxr-xr-x  7 root root 4096 Jan  8 14:21 linux-headers-3.13.0-106-generic
drwxr-xr-x 24 root root 4096 Jun 16  2014 linux-headers-3.13.0-24
drwxr-xr-x  7 root root 4096 Jun 16  2014 linux-headers-3.13.0-24-generic
drwxr-xr-x 24 root root 4096 Jun 16  2014 linux-headers-3.13.0-29
drwxr-xr-x  7 root root 4096 Jun 16  2014 linux-headers-3.13.0-29-generic
drwxr-xr-x 24 root root 4096 Aug  6  2014 linux-headers-3.13.0-32
drwxr-xr-x  7 root root 4096 Aug  6  2014 linux-headers-3.13.0-32-generic
drwxr-xr-x 24 root root 4096 Aug 19  2014 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 19  2014 linux-headers-3.13.0-34-generic
drwxr-xr-x 27 root root 4096 Jan  8 17:32 linux-headers-4.4.0-57
drwxr-xr-x  7 root root 4096 Jan  8 17:32 linux-headers-4.4.0-57-generic
```

ls -al /lib/modules/
```
total 32
drwxr-xr-x  8 root root 4096 Jan  8 19:19 .
drwxr-xr-x 25 root root 4096 Jan  8 17:20 ..
drwxr-xr-x  5 root root 4096 Jan  8 14:22 3.13.0-106-generic
drwxr-xr-x  5 root root 4096 Jun 16  2014 3.13.0-24-generic
drwxr-xr-x  5 root root 4096 Jun 16  2014 3.13.0-29-generic
drwxr-xr-x  5 root root 4096 Aug  6  2014 3.13.0-32-generic
drwxr-xr-x  5 root root 4096 Aug 19  2014 3.13.0-34-generic
drwxr-xr-x  5 root root 4096 Jan  8 18:47 4.4.0-57-generic
```

ls -al /boot/
```
total 272744
drwxr-xr-x  3 root root     4096 Jan 11 12:51 .
drwxr-xr-x 24 root root     4096 Jan  8 17:56 ..
-rw-r--r--  1 root root  1166834 Dec  6 11:22 abi-3.13.0-106-generic
-rw-r--r--  1 root root  1158016 May  2  2014 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1161764 Jun  4  2014 abi-3.13.0-29-generic
-rw-r--r--  1 root root  1162712 Jul 14  2014 abi-3.13.0-32-generic
-rw-r--r--  1 root root  1162712 Aug 13  2014 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1243800 Dec  9 22:04 abi-4.4.0-57-generic
-rw-r--r--  1 root root      512 Jan  8 14:11 boot.0800
-rw-r--r--  1 root root      512 Aug 19 22:19 boot.0810
-rw-r--r--  1 root root      512 Aug 19 22:19 boot.0820
-rw-r--r--  1 root root   113162 Jan  8 18:46 coffee.bmp
-rw-r--r--  1 root root   166061 Dec  6 11:22 config-3.13.0-106-generic
-rw-r--r--  1 root root   165510 May  2  2014 config-3.13.0-24-generic
-rw-r--r--  1 root root   165544 Jun  4  2014 config-3.13.0-29-generic
-rw-r--r--  1 root root   165611 Jul 14  2014 config-3.13.0-32-generic
-rw-r--r--  1 root root   165611 Aug 13  2014 config-3.13.0-34-generic
-rw-r--r--  1 root root   189991 Dec  9 22:04 config-4.4.0-57-generic
-rw-r--r--  1 root root    22466 Jan  8 18:46 debian.bmp
-rw-r--r--  1 root root    22560 Jan  8 18:46 debian-de.bmp
-rw-r--r--  1 root root    31628 Jan  8 18:46 debianlilo.bmp
drwxr-xr-x  5 root root     4096 Jan 11 12:55 grub
-rw-r--r--  1 root root 31561136 Jan  8 17:56 initrd.img-3.13.0-106-generic
-rw-r--r--  1 root root 19283005 Jan  8 16:54 initrd.img-3.13.0-106-generic.dpkg-bak
-rw-r--r--  1 root root 19118785 Jan  8 14:14 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 19124435 Jan  8 14:13 initrd.img-3.13.0-29-generic
-rw-r--r--  1 root root 19180417 Jan  8 14:12 initrd.img-3.13.0-32-generic
-rw-r--r--  1 root root 19181265 Jan  8 14:12 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root  9542090 Jan 11 12:51 initrd.img-3.13.0-93-generic
-rw-r--r--  1 root root 37960579 Jan  8 19:11 initrd.img-4.4.0-57-generic
-rw-r--r--  1 root root 37960744 Jan  8 18:47 initrd.img-4.4.0-57-generic.dpkg-bak
-rw-r--r--  1 root root    22578 Jan  8 18:46 inside.bmp
-rw-------  1 root root   512000 Jan  8 14:23 map
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root     6878 Jan  8 18:46 onlyblue.bmp
-rw-------  1 root root  3399674 Dec  6 11:22 System.map-3.13.0-106-generic
-rw-------  1 root root  3372643 May  2  2014 System.map-3.13.0-24-generic
-rw-------  1 root root  3378267 Jun  4  2014 System.map-3.13.0-29-generic
-rw-------  1 root root  3381262 Jul 14  2014 System.map-3.13.0-32-generic
-rw-------  1 root root  3381262 Aug 13  2014 System.map-3.13.0-34-generic
-rw-------  1 root root  3875329 Dec  9 22:04 System.map-4.4.0-57-generic
-rw-r--r--  1 root root    33192 Jan  8 18:46 tuxlogo.bmp
-rw-------  1 root root  5849616 Dec  6 11:22 vmlinuz-3.13.0-106-generic
-rw-------  1 root root  5776416 May  2  2014 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5792544 Jun  4  2014 vmlinuz-3.13.0-29-generic
-rw-------  1 root root  5798112 Jul 14  2014 vmlinuz-3.13.0-32-generic
-rw-------  1 root root  5797728 Aug 13  2014 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  7067152 Dec  9 22:04 vmlinuz-4.4.0-57-generic
```

dpkg -l | grep linux-
```
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
iF  linux-firmware                                        1.157.6                                       all          Firmware for Linux kernel drivers
iU  linux-generic                                         4.4.0.57.60                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-106                              3.13.0-106.153                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-106-generic                      3.13.0-106.153                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                                4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                        4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.57.60                                   amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rH  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                                   4.4.0.57.60                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-57.78                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2017-01-11
Mista G Nerdl Ho Kay !

Now I do not understand the why :
> 
-rw-r--r--  1 root root    22466 Jan  8 18:46 debian.bmp
-rw-r--r--  1 root root    22560 Jan  8 18:46 debian-de.bmp
-rw-r--r--  1 root root    31628 Jan  8 18:46 debianlilo.bmp

should exist, appears to be lilo related and as such for the time being I am going to ignore them .

Let's do:
```

sudo rm /boot/initrd.img-3.13.0-93-generic
sudo apt -f install
sudo apt-get autoremove linux-{headers,image}-3.13.0-93*

```

If these run clean then we want to properly install the kernel meta packages :
```

sudo apt install --reinstall linux-generic linux-image-generic

``` here with the expectation of pulling in the 4.4.0-57 kernel .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-11
sudo rm /boot/initrd.img-3.13.0-93-generic

no return...so it was deleted. To be certain I ran it again, and recived "no such file or directory".

sudo apt -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-93-generic
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
8 not fully installed or removed.
After this operation, 152 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 446039 files and directories currently installed.)
Removing linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-93-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
WARNING: missing /lib/modules/3.13.0-93-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-93-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_BKtoNl/lib/modules/3.13.0-93-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_BKtoNl/lib/modules/3.13.0-93-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Fatal: open /boot/vmlinuz-3.13.0-93-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
dpkg: error processing package linux-image-extra-3.13.0-93-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-3.13.0-93-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

sudo apt-get autoremove linux-{headers,image}-3.13.0-93*
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-image-3.13.0-93-generic' for glob 'linux-image-3.13.0-93*'
Package 'linux-image-3.13.0-93-generic' is not installed, so not removed
E: Unable to locate package linux-headers-3.13.0-93*
E: Couldn't find any package by glob 'linux-headers-3.13.0-93*'
E: Couldn't find any package by regex 'linux-headers-3.13.0-93*'
```

Alot of the errors seem to be caused by -93 not being fully installed. Can I reinstall it then uninstall?

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Ouch !

There is a lot I do not know . But in this case what could be calling the -93 kernel is a mystery to me !
Help me up on the learning curve !
In the interest of getting this done, let's move it on along .
Sure worth a shot to re-install the -93 kernel - as the safer thing to try: - give the system what it wants -
But it is getting dicey to do so as you are now on the xenial release and the -93 kernel is of trusty, that you no longer have access to the repo .
To compound the problem - for me - I had expected to find the kernel at:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Nope, not there !

Now pardon my lack of knowledge - to install the -93 all I know to try is attempt to obtain the 4 individual packages from the source :
starting at:
 [http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93](http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93)

I will welcome others opinions on this method to resolve. Mista, what are your thoughts ? Comfortable to try and see what results ? Be aware I have yet to be here - 1st time for everything . Just do not know what will happen on attempting a fresh install of a trusty kernel in a xenial install !

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Ouch !

There is a lot I do not know . But in this case what could be calling the -93 kernel is a mystery to me !
Help me up on the learning curve !
In the interest of getting this done, let's move it on along .
Sure worth a shot to re-install the -93 kernel - as the safer thing to try: - give the system what it wants -
But it is getting dicey to do so as you are now on the xenial release and the -93 kernel is of trusty, that you no longer have access to the repo .
To compound the problem - for me - I had expected to find the kernel at:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Nope, not there !

Now pardon my lack of knowledge - to install the -93 all I know to try is attempt to obtain the 4 individual packages from the source :
starting at:
 [http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93](http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93)

I will welcome others opinions on this method to resolve. Mista, what are your thoughts ? Comfortable to try and see what results ? Be aware I have yet to be here - 1st time for everything . Just do not know what will happen on attempting a fresh install of a trusty kernel in a xenial install !

[INDENT][INDENT]sometimes I do wonder[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-11
Soo... after some frustration I had a screw it all moment and decided to reinstall then uninstall. Which was found to work here
[http://askubuntu.com/questions/652299/need-help-removing-linux-image-3-16-0-34-generic-and-linux-image-extra-3-16-0-34](http://askubuntu.com/questions/652299/need-help-removing-linux-image-3-16-0-34-generic-and-linux-image-extra-3-16-0-34)

Ok I went to Synaptic and added 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates restricted main multiverse universe

to my repositories then reinstalled using 

sudo apt-get install --reinstall linux-image-3.13.0-93-generic linux-headers-3.13.0-93-generic linux-image-extra-3.13.0-93-generic
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-3.13.0-93
Suggested packages:
  fdutils linux-doc-3.13.0 | linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.13.0-93 linux-headers-3.13.0-93-generic
  linux-image-3.13.0-93-generic
0 upgraded, 3 newly installed, 1 reinstalled, 0 to remove and 16 not upgraded.
8 not fully installed or removed.
Need to get 61.6 MB of archives.
After this operation, 120 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu trusty-updates/main amd64 linux-image-3.13.0-93-generic amd64 3.13.0-93.140 [15.3 MB]
Get:2 http://archive.ubuntu.com/ubuntu trusty-updates/main amd64 linux-image-extra-3.13.0-93-generic amd64 3.13.0-93.140 [36.7 MB]
Get:3 http://archive.ubuntu.com/ubuntu trusty-updates/main amd64 linux-headers-3.13.0-93 all 3.13.0-93.140 [8,885 kB]
Get:4 http://archive.ubuntu.com/ubuntu trusty-updates/main amd64 linux-headers-3.13.0-93-generic amd64 3.13.0-93.140 [700 kB]
Fetched 61.6 MB in 19s (3,117 kB/s)                                            
Selecting previously unselected package linux-image-3.13.0-93-generic.
(Reading database ... 446040 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-93-generic_3.13.0-93.140_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-93-generic (3.13.0-93.140) ...
Selecting previously unselected package linux-image-extra-3.13.0-93-generic.
Preparing to unpack .../linux-image-extra-3.13.0-93-generic_3.13.0-93.140_amd64.deb ...
Unpacking linux-image-extra-3.13.0-93-generic (3.13.0-93.140) over (3.13.0-93.140) ...
Selecting previously unselected package linux-headers-3.13.0-93.
Preparing to unpack .../linux-headers-3.13.0-93_3.13.0-93.140_all.deb ...
Unpacking linux-headers-3.13.0-93 (3.13.0-93.140) ...
Selecting previously unselected package linux-headers-3.13.0-93-generic.
Preparing to unpack .../linux-headers-3.13.0-93-generic_3.13.0-93.140_amd64.deb ...
Unpacking linux-headers-3.13.0-93-generic (3.13.0-93.140) ...
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up lilo (1:24.2-1) ...
Running lilo...
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
dpkg: error processing package lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-57-generic
) points to /boot/initrd.img-4.4.0-57-generic
 (/boot/initrd.img-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-57-generic
) points to /boot/vmlinuz-4.4.0-57-generic
 (/boot/vmlinuz-4.4.0-57-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-genericNo apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          No apport report written because MaxReports is reached already
                                         depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-3.13.0-93-generic (3.13.0-93.140) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-93-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-93-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-93-generic:
 linux-image-extra-3.13.0-93-generic depends on linux-image-3.13.0-93-generic; however:
  Package linux-image-3.13.0-93-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-93-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-3.13.0-93 (3.13.0-93.140) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up linux-headers-3.13.0-93-generic (3.13.0-93.140) ...
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 lilo
 linux-firmware
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
 linux-image-3.13.0-93-generic
 linux-image-extra-3.13.0-93-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

sudo apt-get remove linux-image-3.16.0-34-generic linux-headers-3.16.0-34-generic linux-image-extra-3.16.0-34-generic
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-headers-3.16.0-34-generic' is not installed, so not removed
Package 'linux-image-3.16.0-34-generic' is not installed, so not removed
Package 'linux-image-extra-3.16.0-34-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
9 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up lilo (1:24.2-1) ...
Running lilo...
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
dpkg: error processing package lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-3.13.0-93-generic (3.13.0-93.140) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-3.13.0-93-generic
) points to /boot/initrd.img-3.13.0-93-generic
 (/boot/initrd.img-3.13.0-93-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-93-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-3.13.0-93-generic
) points to /boot/vmlinuz-3.13.0-93-generic
 (/boot/vmlinuz-3.13.0-93-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-3.13.0-93-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-93-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-93-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-imaNo apport report written because MaxReports is reached already
                      No apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              ge-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-93-generic:
 linux-image-extra-3.13.0-93-generic depends on linux-image-3.13.0-93-generic; however:
  Package linux-image-3.13.0-93-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-93-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 lilo
 linux-image-3.13.0-93-generic
 linux-firmware
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.13.0-93-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

So it didn't work, and I may have made it worse....i dunno. to find out I disabled the old repositories. Then after a source update.

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libpurple-bin linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  apt apt-transport-https apt-utils gir1.2-javascriptcoregtk-4.0
  gir1.2-webkit2-4.0 libapt-inst2.0 libapt-pkg5.0 libjavascriptcoregtk-4.0-18
  libvncclient1 libwebkit2gtk-4.0-37 libwebkit2gtk-4.0-37-gtk2 linux-libc-dev
12 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
9 not fully installed or removed.
Need to get 2,081 kB/25.2 MB of archives.
After this operation, 6,098 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-pkg5.0 amd64 1.2.18 [707 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libapt-inst2.0 amd64 1.2.18 [55.6 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt amd64 1.2.18 [1,042 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-utils amd64 1.2.18 [196 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 apt-transport-https amd64 1.2.18 [26.0 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libvncclient1 amd64 0.9.10+dfsg-3ubuntu0.16.04.1 [54.3 kB]
Fetched 2,081 kB in 12s (169 kB/s)                                             
(Reading database ... 475685 files and directories currently installed.)
Preparing to unpack .../libapt-pkg5.0_1.2.18_amd64.deb ...
Unpacking libapt-pkg5.0:amd64 (1.2.18) over (1.2.15ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up libapt-pkg5.0:amd64 (1.2.18) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
(Reading database ... 475685 files and directories currently installed.)
Preparing to unpack .../libapt-inst2.0_1.2.18_amd64.deb ...
Unpacking libapt-inst2.0:amd64 (1.2.18) over (1.2.15ubuntu0.2) ...
Preparing to unpack .../archives/apt_1.2.18_amd64.deb ...
Unpacking apt (1.2.18) over (1.2.15ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up apt (1.2.18) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
(Reading database ... 475685 files and directories currently installed.)
Preparing to unpack .../apt-utils_1.2.18_amd64.deb ...
Unpacking apt-utils (1.2.18) over (1.2.15ubuntu0.2) ...
Preparing to unpack .../apt-transport-https_1.2.18_amd64.deb ...
Unpacking apt-transport-https (1.2.18) over (1.2.15ubuntu0.2) ...
Preparing to unpack .../libwebkit2gtk-4.0-37-gtk2_2.14.2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.2-0ubuntu0.16.04.1) over (2.12.5-0ubuntu0.16.04.1) ...
Preparing to unpack .../libwebkit2gtk-4.0-37_2.14.2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libwebkit2gtk-4.0-37:amd64 (2.14.2-0ubuntu0.16.04.1) over (2.12.5-0ubuntu0.16.04.1) ...
Preparing to unpack .../libjavascriptcoregtk-4.0-18_2.14.2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking libjavascriptcoregtk-4.0-18:amd64 (2.14.2-0ubuntu0.16.04.1) over (2.12.5-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-webkit2-4.0_2.14.2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking gir1.2-webkit2-4.0:amd64 (2.14.2-0ubuntu0.16.04.1) over (2.12.5-0ubuntu0.16.04.1) ...
Preparing to unpack .../gir1.2-javascriptcoregtk-4.0_2.14.2-0ubuntu0.16.04.1_amd64.deb ...
Unpacking gir1.2-javascriptcoregtk-4.0:amd64 (2.14.2-0ubuntu0.16.04.1) over (2.12.5-0ubuntu0.16.04.1) ...
Preparing to unpack .../libvncclient1_0.9.10+dfsg-3ubuntu0.16.04.1_amd64.deb ...
Unpacking libvncclient1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) over (0.9.10+dfsg-3build1) ...
Preparing to unpack .../linux-libc-dev_4.4.0-59.80_amd64.deb ...
Unpacking linux-libc-dev:amd64 (4.4.0-59.80) over (4.4.0-57.78) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up lilo (1:24.2-1) ...
Running lilo...
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
dpkg: error processing package lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-3.13.0-93-generic (3.13.0-93.140) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.13.0-93-generic.postinst line 1025.
dpkg: error processing package linux-image-3.13.0-93-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package linux-firmware (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-57-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-57-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-57-generic:
 linux-image-extra-4.4.0-57-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-57-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-57-generic; however:
  Package linux-image-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-57-generic; however:
  Package linux-image-extra-4.4.0-57-generic is not configured yet.
 linux-image-generic depends on linux-firmware; however:
  Package linux-firmware is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.57.60); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-3.13.0-93-generic:
 linux-image-extra-3.13.0-93-generic depends on linux-image-3.13.0-93-generic; however:
  Package linux-image-3.13.0-93-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.13.0-93-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up libapt-inst2.0:amd64 (1.2.18) ...
Setting up apt-utils (1.2.18) ...
Setting up apt-transport-https (1.2.18) ...
Setting up libjavascriptcoregtk-4.0-18:amd64 (2.14.2-0ubuntu0.16.04.1) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.14.2-0ubuntu0.16.04.1) ...
Setting up libwebkit2gtk-4.0-37-gtk2:amd64 (2.14.2-0ubuntu0.16.04.1) ...
Setting up gir1.2-javascriptcoregtk-4.0:amd64 (2.14.2-0ubuntu0.16.04.1) ...
Setting up gir1.2-webkit2-4.0:amd64 (2.14.2-0ubuntu0.16.04.1) ...
Setting up libvncclient1:amd64 (0.9.10+dfsg-3ubuntu0.16.04.1) ...
Setting up linux-libc-dev:amd64 (4.4.0-59.80) ...
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
Added Linux  *
Fatal: open /boot/vmlinuz-3.13.0-35-generic: No such file or directory
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 lilo
 linux-image-3.13.0-93-generic
 linux-firmware
 linux-image-4.4.0-57-generic
 linux-image-extra-4.4.0-57-generic
 linux-image-generic
 linux-generic
 linux-image-extra-3.13.0-93-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

so crap...i made it worse....

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Ouch !

There is a lot I do not know . But in this case what could be calling the -93 kernel is a mystery to me !
Help me up on the learning curve !
In the interest of getting this done, let's move it on along .
Sure worth a shot to re-install the -93 kernel - as the safer thing to try: - give the system what it wants -
But it is getting dicey to do so as you are now on the xenial release and the -93 kernel is of trusty, that you no longer have access to the repo .
To compound the problem - for me - I had expected to find the kernel at:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Nope, not there !

Now pardon my lack of knowledge - to install the -93 all I know to try is attempt to obtain the 4 individual packages from the source :
starting at:
 [http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93](http://packages.ubuntu.com/trusty-updates/linux-headers-3.13.0-93)

I will welcome others opinions on this method to resolve. Mista, what are your thoughts ? Comfortable to try and see what results ? Be aware I have yet to be here - 1st time for everything . Just do not know what will happen on attempting a fresh install of a trusty kernel in a xenial install !

[INDENT][INDENT]sometimes I do wonder[/INDENT][/INDENT]

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Hummmm ...

How about we bite on a bullet and remove lilo at this time . See if it is lilo that is attempting to pull in those old kernels ?
```

sudo apt-get purge --auto-remove lilo
sudo apt update
sudo apt upgrade

```
then see what we can do with the -35 and -93 kernels .
The "  Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo" problem I was aware of; just had not gotten to it yet .

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]gots to be a way[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ubfan1 on 2017-01-11
You're not the first person with this problem.  I've had it myself once.  I repeat, the solution is to make the package manager happy (and whatever system files it runs) by supplying the missing directories and files it complains about.  Whatever script is failing, and complaining about a missing file, make a zero length file with touch and try again.  I'd ignore the /var/tmp... stuff until last, those are generated and will probably go away by themselves when the earlier problems are fixed.

---

### Post by Mista G Nerd on 2017-01-11
sudo apt-get purge --auto-remove lilo
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lilo*
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
9 not fully installed or removed.
After this operation, 671 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 475684 files and directories currently installed.)
Removing lilo (1:24.2-1) ...
Purging configuration files for lilo (1:24.2-1) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-3.13.0-93-generic (3.13.0-93.140) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-106-generic
Found initrd image: /boot/initrd.img-3.13.0-106-generic
Found linux image: /boot/vmlinuz-3.13.0-93-generic
Found initrd image: /boot/initrd.img-3.13.0-93-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-firmware (1.157.6) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
update-initramfs: Generating /boot/initrd.img-3.13.0-106-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-24-generic
Setting up linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-106-generic
Found initrd image: /boot/initrd.img-3.13.0-106-generic
Found linux image: /boot/vmlinuz-3.13.0-93-generic
Found initrd image: /boot/initrd.img-3.13.0-93-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-106-generic
Found initrd image: /boot/initrd.img-3.13.0-106-generic
Found linux image: /boot/vmlinuz-3.13.0-93-generic
Found initrd image: /boot/initrd.img-3.13.0-93-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (4.4.0.57.60) ...
Setting up linux-generic (4.4.0.57.60) ...
Setting up linux-image-extra-3.13.0-93-generic (3.13.0-93.140) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-93-generic /boot/vmlinuz-3.13.0-93-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-106-generic
Found initrd image: /boot/initrd.img-3.13.0-106-generic
Found linux image: /boot/vmlinuz-3.13.0-93-generic
Found initrd image: /boot/initrd.img-3.13.0-93-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found linux image: /boot/vmlinuz-3.13.0-29-generic
Found initrd image: /boot/initrd.img-3.13.0-29-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Processing triggers for initramfs-tools (0.122ubuntu8.7) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo
```

sudo apt-get update
```
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease       
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [184 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [126 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [151 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:10 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:12 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:13 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.1 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.0 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [25.4 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [31.7 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [208 B]
Fetched 1,241 kB in 7s (157 kB/s)                                              
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
```

sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libpurple-bin linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```

.... I think it worked.... no errors. I'm going to try to install an app. It wouldn't let me do that before!

sudo add-apt-repository --yes ppa:js-reynaud/kicad-4
```
gpg: keyring `/tmp/tmp073zf97_/secring.gpg' created
gpg: keyring `/tmp/tmp073zf97_/pubring.gpg' created
gpg: requesting key 910F124E from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp073zf97_/trustdb.gpg: trustdb created
gpg: key 910F124E: public key "Launchpad PPA for j2010" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```

sudo apt update
```
Get:1 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial InRelease [17.6 kB]
Get:2 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main amd64 Packages [5,640 B]
Get:3 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main i386 Packages [5,640 B]
Get:4 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main Translation-en [1,852 B]
Hit:5 http://archive.ubuntu.com/ubuntu xenial InRelease         
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]      
Fetched 337 kB in 6s (49.5 kB/s)                                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
```


apt list --upgradable
```
Listing... Done
libpurple-bin/xenial-updates,xenial-updates,xenial-security,xenial-security 1:2.10.12-0ubuntu5.1 all [upgradable from: 1:2.10.9-0ubuntu3.3]
linux-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
linux-image-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
```

sudo apt install kicad
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  kicad-doc-en kicad-library libboost-context1.58.0
Suggested packages:
  extra-xdg-menus kicad-demo kicad-locale-ko | kicad-locale-ru
  | kicad-locale-pl | kicad-locale-pt | kicad-locale-ja | kicad-locale-id
  | kicad-locale-ca | kicad-locale-it | kicad-locale-el | kicad-locale-zh
  | kicad-locale-de | kicad-locale-sl | kicad-locale-cs | kicad-locale-bg
  | kicad-locale-sv | kicad-locale-lt | kicad-locale-fi | kicad-locale-fr
  | kicad-locale-hu | kicad-locale-nl | kicad-locale-es | kicad-locale-sk
The following NEW packages will be installed:
  kicad kicad-doc-en kicad-library libboost-context1.58.0
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
Need to get 114 MB of archives.
After this operation, 664 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main amd64 kicad amd64 4.0.5+e0-6337~49~ubuntu16.04.1 [13.9 MB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 libboost-context1.58.0 amd64 1.58.0+dfsg-5ubuntu3.1 [18.9 kB]
Get:3 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main amd64 kicad-doc-en all 4.0.5+e1+1166~16~ubuntu16.04.1 [55.3 MB]
Get:4 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial/main amd64 kicad-library all 4.0.5+e0+1097~2~ubuntu16.04.1 [44.9 MB]
Fetched 114 MB in 34s (3,327 kB/s)                                             
Selecting previously unselected package libboost-context1.58.0:amd64.
(Reading database ... 475627 files and directories currently installed.)
Preparing to unpack .../libboost-context1.58.0_1.58.0+dfsg-5ubuntu3.1_amd64.deb ...
Unpacking libboost-context1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Selecting previously unselected package kicad.
Preparing to unpack .../kicad_4.0.5+e0-6337~49~ubuntu16.04.1_amd64.deb ...
Unpacking kicad (4.0.5+e0-6337~49~ubuntu16.04.1) ...
Selecting previously unselected package kicad-doc-en.
Preparing to unpack .../kicad-doc-en_4.0.5+e1+1166~16~ubuntu16.04.1_all.deb ...
Unpacking kicad-doc-en (4.0.5+e1+1166~16~ubuntu16.04.1) ...
Selecting previously unselected package kicad-library.
Preparing to unpack .../kicad-library_4.0.5+e0+1097~2~ubuntu16.04.1_all.deb ...
Unpacking kicad-library (4.0.5+e0+1097~2~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for shared-mime-info (1.5-2ubuntu0.1) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Setting up libboost-context1.58.0:amd64 (1.58.0+dfsg-5ubuntu3.1) ...
Setting up kicad (4.0.5+e0-6337~49~ubuntu16.04.1) ...
Setting up kicad-doc-en (4.0.5+e1+1166~16~ubuntu16.04.1) ...
Setting up kicad-library (4.0.5+e0+1097~2~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu5) ...
```


Woohoo! I think you've solved my problem thankyou!

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Uh HUh ..

Looks like it was lilo at the root of it all !

We still have some unfinished stuff to attend to .
Show a new :
```

dpkg -l | grep linux

```
in the mix is still " Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1.bin for module i915_bpo " .

clean
[INDENT][INDENT][INDENT]make it so
[/INDENT][/INDENT][/INDENT]

---

### Post by geeksmith on 2017-01-11
If you're feeling lucky, you can install grub using the commands below. If for some reason this doesn't work (i.e. your system setup is atypical) you'll need a live Ubuntu DVD to rescue your system and install LILO. It's highly unlikely that replacing the booloader will erase data on partitions, but I don't know your system like you do, so use it at your own risk.

```

sudo apt install grub2
sudo grub-mkdevicemap
sudo grub-install /dev/YOURDISK
sudo update-grub

```

---

### Post by Mista G Nerd on 2017-01-11
dpkg -l | grep linux```

ii  console-setup-linux                                   1.108ubuntu15.2                               all          Linux specific part of console-setup
ii  libselinux1:amd64                                     2.4-3build2                                   amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                      2.4-3build2                                   i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                        1.10.0-1                                      amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                         1.10.0-1                                      i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                                  1.10.0-1                                      amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                                   1.10.0-1                                      i386         Video4linux frame format conversion library
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                        1.157.6                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                         4.4.0.57.60                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-106                              3.13.0-106.153                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-106-generic                      3.13.0-106.153                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                                4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                        4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.57.60                                   amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.57.60                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-59.80                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  playonlinux                                           4.2.10-2ubuntu0.1                             all          front-end for Wine
ii  pptp-linux                                            1.8.0-1                                       amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                              3:6.03+dfsg-11ubuntu1                         amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                            2.27.1-6ubuntu3.1                             amd64        miscellaneous system utilities
```


What is the recommended procedure to installing Win 10 alongside Ubuntu?

---

### Post by Bashing-om on 2017-01-11
Mista G Nerd; Gunn ...

That all looks good now .. all are 'ii'  in that 1st field - did you re-install the meta packages to resolve ?
Let's get prepared to reboot the machine . what shows for booting ?
```

ls -al /vmlinuz* /initrd.img*

```
Just a bit of concern however, as the 4.4.0-59 kernel is out and you do not have it installed:
> 
sysop@x1604:~$ uname -r
4.4.0-59-generic
sysop@x1604:~$ 


[INDENT][INDENT]squeeky clean
[INDENT][INDENT][INDENT]w like it like that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-12
Wow! It booted cleanly today, no problems.

ls -al /vmlinuz* /initrd.img*
```
lrwxrwxrwx 1 root root 32 Jan 11 18:22 /initrd.img -> boot/initrd.img-4.4.0-57-generic
lrwxrwxrwx 1 root root 33 Jan 11 18:21 /initrd.img.old -> boot/initrd.img-3.13.0-93-generic
lrwxrwxrwx 1 root root 29 Jan 11 18:22 /vmlinuz -> boot/vmlinuz-4.4.0-57-generic
lrwxrwxrwx 1 root root 30 Jan 11 18:21 /vmlinuz.old -> boot/vmlinuz-3.13.0-93-generic
```

---

### Post by Bashing-om on 2017-01-12
Mista G Nerd; Ho Kay !

Making good progress.
Let's next get you up on the -59 kernel and get rid of that problematic " -3.13.0-93-generic " kernel.

What (also) does the system report as the booting kernel:
```

uname -a
apt list linux-image-generic

```
We get ya up on the -59 kernel then we clean up and call it all good .

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-12
uname -a
```
4.4.0-57-generic #78-Ubuntu SMP Fri Dec 9 23:50:32 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

apt list linux-image-generic
```
Listing... Done
linux-image-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
N: There are 2 additional versions. Please use the '-a' switch to see them.
```

---

### Post by Bashing-om on 2017-01-12
Mista G Nerd; K;

Looks good. try and get the -59 kernel:
```

sudo apt update
sudo apt full-upgrade

```
If that runs clean, then it is time for clean up :)

[INDENT][INDENT]nothing smells like
[INDENT][INDENT][INDENT]a booted updated system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-13
sudo apt update
```
Hit:1 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu xenial InRelease
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]
Get:5 http://archive.ubuntu.com/ubuntu xenial-security InRelease [102 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main Sources [215 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [117 kB]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages [452 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main i386 Packages [444 kB]
Get:10 https://content.runescape.com/downloads/ubuntu trusty InRelease [2,236 B]
Get:11 http://archive.ubuntu.com/ubuntu xenial-updates/main Translation-en [178 kB]
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [193 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [378 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [373 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [140 kB]
Get:17 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [127 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [154 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:20 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:21 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:22 http://archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Get:23 http://archive.ubuntu.com/ubuntu xenial-security/main Sources [54.5 kB]
Get:24 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages [201 kB]
Get:25 http://archive.ubuntu.com/ubuntu xenial-security/main i386 Packages [195 kB]
Get:26 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.0 kB]
Get:27 http://archive.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:28 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [69.3 kB]
Get:29 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [65.5 kB]
Get:30 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [25.4 kB]
Get:31 http://archive.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [31.8 kB]
Get:32 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 4,141 kB in 2s (1,492 kB/s)                       
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
13 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: https://content.runescape.com/downloads/ubuntu/dists/trusty/InRelease: Signature by key AAC9264309E4D717441DB9527373B12CE03BEB4B uses weak digest algorithm (SHA1)
```

sudo apt list --upgradable
```
Listing... Done
initramfs-tools/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.7]
initramfs-tools-bin/xenial-updates 0.122ubuntu8.8 amd64 [upgradable from: 0.122ubuntu8.7]
initramfs-tools-core/xenial-updates,xenial-updates 0.122ubuntu8.8 all [upgradable from: 0.122ubuntu8.7]
libpurple-bin/xenial-updates,xenial-updates,xenial-security,xenial-security 1:2.10.12-0ubuntu5.1 all [upgradable from: 1:2.10.9-0ubuntu3.3]
linux-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
linux-headers-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
linux-image-generic/xenial-updates,xenial-security 4.4.0.59.62 amd64 [upgradable from: 4.4.0.57.60]
overlay-scrollbar/xenial-updates,xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 all [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
overlay-scrollbar-gtk2/xenial-updates 0.2.17.1+16.04.20151117-0ubuntu1.16.04.1 amd64 [upgradable from: 0.2.17.1+16.04.20151117-0ubuntu1]
python3-update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.4]
update-manager/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.4]
update-manager-core/xenial-updates,xenial-updates 1:16.04.5 all [upgradable from: 1:16.04.4]
xdg-utils/xenial-updates,xenial-updates 1.1.1-1ubuntu1.16.04.1 all [upgradable from: 1.1.1-1ubuntu1]
```

Ok something happened during the upgrade. I went AFK for 3 minutes (bathroom break), and upon returning saw that the a few of the apps I was running had crashed. With error boxes all over my screen. In the terminal was a list of packages starting with "lib" and some error. But while closing error boxes I accidentally closed the terminal so I don't know what error was returned. However I opened a new terminal and run the upgrade again and this is what it returned 

sudo apt full-upgrade
```
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
```

sudo dpkg --configure -a
```
dpkg: error: unable to access dpkg status area: Read-only file system
```

---

### Post by Bashing-om on 2017-01-13
Mista G Nerd; Yuk;

Well, maybe not too bad of a situation .
but " Read-only file system" is cause for concern.

Have you rebooted and still with a RO file system ?
If so we need to run a file system check . This check can be done from the install a couple of ways, but I do prefer to run checks from a live environment. Do you have a liveDVD(USB) on hand ?

[INDENT][INDENT]were not for this luck
[INDENT][INDENT][INDENT]would have no luck at all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-13
Ok just failed to boot.

this is what i received
```
No Caching mode found
Assuming drive cache: write through /dev/sda1 contains a filesystem with errors. check forced
Inodes that were part of a corrupted orphaned linked list found.

/dev/sda1: UNEXPECTED INCONSISTENCY: RUN fsck MANUALLY (i.e.. without -a or -p options)
fsk exited with status code 4
The root filesystem on /dev/sda1 requires manual fsck

Busybox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) built-in shell (ash)
Enter 'help' for a list of commands

(initramfs)
```

---

### Post by Bashing-om on 2017-01-13
Mista G Nerd; Hey !

Not to despair, yet .


My last :
> 
Do you have a liveDVD(USB) on hand ?

As it is my thought the return from a live environment is the better . If ya gots a liveDVD(USB) on-hand .
Else in 16.04 we can force a file system check ( simplistic) from the grub boot directives .
So, how do you want to proceed here ?

[INDENT][INDENT]the possible we do quick
[INDENT][INDENT]the impossible takes a bit longer
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-13
Actually i do have a live persistent usb.

---

### Post by Bashing-om on 2017-01-13
Mista G Nerd: Great !

Same same as the installed version - more reliable - ?
run from the liveUSB:
so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)
[code]

[INDENT][INDENT]fsck is some kind of smart
[INDENT][INDENT][INDENT]smarter 'bout the file system than I
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-14
sudo e2fsck -C0 -p -f -v /dev/sda1
```
/dev/sda1:                                                                      Inodes that were part of a corrupted orphan linked list found.  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
```

sudo e2fsck -f -y -v /dev/sda1
```
e2fsck 1.42.13 (17-May-2015)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix? yes

Inode 393327 was part of the orphaned inode list.  FIXED.
Inode 403527 was part of the orphaned inode list.  FIXED.
Inode 655977 was part of the orphaned inode list.  FIXED.
Inode 655994 was part of the orphaned inode list.  FIXED.
Inode 656007 was part of the orphaned inode list.  FIXED.
Deleted inode 656032 has zero dtime.  Fix? yes

Inode 656457 was part of the orphaned inode list.  FIXED.
Inode 656653 was part of the orphaned inode list.  FIXED.
Inode 656724 was part of the orphaned inode list.  FIXED.
Inode 657476 was part of the orphaned inode list.  FIXED.
Inode 657481 was part of the orphaned inode list.  FIXED.
Inode 657485 was part of the orphaned inode list.  FIXED.
Inode 658899 was part of the orphaned inode list.  FIXED.
Inode 662840 was part of the orphaned inode list.  FIXED.
Inode 662846 was part of the orphaned inode list.  FIXED.
Inode 663128 was part of the orphaned inode list.  FIXED.
Inode 663129 was part of the orphaned inode list.  FIXED.
Inode 663130 was part of the orphaned inode list.  FIXED.
Inode 663131 was part of the orphaned inode list.  FIXED.
Inode 663132 was part of the orphaned inode list.  FIXED.
Inode 663133 was part of the orphaned inode list.  FIXED.
Inode 663137 was part of the orphaned inode list.  FIXED.
Inode 663138 was part of the orphaned inode list.  FIXED.
Inode 663139 was part of the orphaned inode list.  FIXED.
Inode 663141 was part of the orphaned inode list.  FIXED.
Inode 663168 was part of the orphaned inode list.  FIXED.
Inode 663170 was part of the orphaned inode list.  FIXED.
Inode 665046 was part of the orphaned inode list.  FIXED.
Inode 665075 was part of the orphaned inode list.  FIXED.
Inode 667611 was part of the orphaned inode list.  FIXED.
Inode 667692 was part of the orphaned inode list.  FIXED.
Inode 667693 was part of the orphaned inode list.  FIXED.
Inode 793611 was part of the orphaned inode list.  FIXED.
Inode 793624 was part of the orphaned inode list.  FIXED.
Inode 793628 was part of the orphaned inode list.  FIXED.
Inode 793630 was part of the orphaned inode list.  FIXED.
Inode 1575289 was part of the orphaned inode list.  FIXED.
Inode 1577547 was part of the orphaned inode list.  FIXED.
Inode 2359315 was part of the orphaned inode list.  FIXED.
Inode 2359321 was part of the orphaned inode list.  FIXED.
Inode 3146247 was part of the orphaned inode list.  FIXED.
Inode 3146249 was part of the orphaned inode list.  FIXED.
Inode 3146255 was part of the orphaned inode list.  FIXED.
Inode 3146256 was part of the orphaned inode list.  FIXED.
Inode 3146258 was part of the orphaned inode list.  FIXED.
Inode 3146260 was part of the orphaned inode list.  FIXED.
Inode 3146262 was part of the orphaned inode list.  FIXED.
Inode 3147570 was part of the orphaned inode list.  FIXED.
Inode 3147571 was part of the orphaned inode list.  FIXED.
Inode 3147572 was part of the orphaned inode list.  FIXED.
Inode 3147573 was part of the orphaned inode list.  FIXED.
Inode 3147574 was part of the orphaned inode list.  FIXED.
Inode 3147575 was part of the orphaned inode list.  FIXED.
Inode 3147582 was part of the orphaned inode list.  FIXED.
Inode 3147583 was part of the orphaned inode list.  FIXED.
Inode 3147726 was part of the orphaned inode list.  FIXED.
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 14155790 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Block bitmap differences:  -(2659008--2659014) -(2702490--2702496) -3155512 -(3218005--3218015) -(3218018--3218024) -(3218080--3218087) -(7397153--7397159) -(11670816--11670832) -(12631651--12631657) +(14614528--14616563) +(14616576--14617015) +(14617024--14617054) +(14617056--14617077) +(14617599--14621685) +(14623362--14623486) +(14623488--14623531) +(14624768--14626813) +(14626816--14627234) +(14627747--14628863) +(14644256--14644334) +(14644847--14645241) +(14645248--14647295) -(17339012--17339018) -(17339038--17339046) -(19974154--19974167) -(19974203--19974209) -(19984429--19984435) -(19984443--19984449) -19984469 -(19984501--19984507) -(19996701--19996707) -(19997134--19997140) -(20004898--20004918) -(20005203--20005223) -(20015678--20015684) -(20513024--20513140) -(20513152--20513168) -(20513920--20514036) -(20877664--20877680) -21012578 -(21012608--21012614) -(21012618--21012644) -(24150362--24150364) -(24150368--24150380) -(24155142--24155148) -(24155439--24155445) -(24155505--24155511) -(24155966--24155986) -(24177946--24177953) -(24177961--24177968) -(25897766--25897845) -(33061548--33061566) -(37489944--37490042) -(37490939--37491411)
Fix? yes

Free blocks count wrong for group #81 (2024, counted=2031).
Fix? yes

Free blocks count wrong for group #82 (8506, counted=8513).
Fix? yes

Free blocks count wrong for group #96 (20750, counted=20751).
Fix? yes

Free blocks count wrong for group #98 (15142, counted=15168).
Fix? yes

Free blocks count wrong for group #225 (17552, counted=17559).
Fix? yes

Free blocks count wrong for group #356 (15529, counted=15546).
Fix? yes

Free blocks count wrong for group #385 (20304, counted=20311).
Fix? yes

Free blocks count wrong for group #529 (12507, counted=12523).
Fix? yes

Free blocks count wrong for group #609 (24933, counted=24976).
Fix? yes

Free blocks count wrong for group #610 (18297, counted=18360).
Fix? yes

Free blocks count wrong for group #626 (7966, counted=8217).
Fix? yes

Free blocks count wrong for group #637 (11967, counted=11984).
Fix? yes

Free blocks count wrong for group #641 (23278, counted=23313).
Fix? yes

Free blocks count wrong for group #737 (8826, counted=8900).
Fix? yes

Free blocks count wrong for group #790 (30239, counted=30319).
Fix? yes

Free blocks count wrong for group #1008 (17672, counted=17691).
Fix? yes

Free blocks count wrong for group #1144 (18921, counted=19493).
Fix? yes

Free blocks count wrong (34412484, counted=34124294).
Fix? yes

Inode bitmap differences:  -393327 -403527 -655977 -655994 -656007 -656032 -656457 -656653 -656724 -657476 -657481 -657485 -658899 -662840 -662846 -(663128--663133) -(663137--663139) -663141 -663168 -663170 -665046 -665075 -667611 -(667692--667693) -793611 -793624 -793628 -793630 -1575289 -1577547 -2359315 -2359321 -3146247 -3146249 -(3146255--3146256) -3146258 -3146260 -3146262 -(3147570--3147575) -(3147582--3147583) -3147726
Fix? yes

Free inodes count wrong for group #48 (791, counted=792).
Fix? yes

Free inodes count wrong for group #49 (5018, counted=5019).
Fix? yes

Free inodes count wrong for group #80 (388, counted=413).
Fix? yes

Free inodes count wrong for group #81 (3205, counted=3210).
Fix? yes

Free inodes count wrong for group #96 (2772, counted=2776).
Fix? yes

Directories count wrong for group #96 (1022, counted=1021).
Fix? yes

Free inodes count wrong for group #192 (678, counted=680).
Fix? yes

Free inodes count wrong for group #288 (639, counted=641).
Fix? yes

Free inodes count wrong for group #384 (1286, counted=1302).
Fix? yes

Free inodes count wrong (11937148, counted=11904760).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

      612616 inodes used (4.89%, out of 12517376)
         911 non-contiguous files (0.1%)
         973 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 546671/450
    15939322 blocks used (31.84%, out of 50063616)
           0 bad blocks
           5 large files

      454216 regular files
       73320 directories
          57 character device files
          25 block device files
           0 fifos
          43 links
       84929 symbolic links (65345 fast symbolic links)
          60 sockets
------------
      612650 files
```

I'll try to boot see what happens.
Ok now i'll continue from where we left off.

sudo apt-get update
```
Hit:1 [http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu](http://ppa.launchpad.net/js-reynaud/kicad-4/ubuntu) xenial InRelease
Get:2 [https://content.runescape.com/downloads/ubuntu](https://content.runescape.com/downloads/ubuntu) trusty InRelease [2,236 B]
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
Fetched 2,236 B in 2s (1,024 B/s)
Reading package lists... Done
W: [https://content.runescape.com/downloads/ubuntu/dists/trusty/InRelease:](https://content.runescape.com/downloads/ubuntu/dists/trusty/InRelease:) Signature by key AAC9264309E4D717441DB9527373B12CE03BEB4B uses weak digest algorithm (SHA1)
```

sudo apt full-upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2017-01-14
Mista G Nerd; Yay !! Looks good !

> 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Let's get a system status :
show
```

sudo apt -f install
sudo dpkg -C
uname -r
dpkg -l | grep linix-

```

[INDENT][INDENT]wiping the sweat of now are we ?
[/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-14
sudo apt -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

sudo dpkg -C
returns nothing.

uname -r
```
4.4.0-59-generic
```

dpkg -l | grep linux-
```
ii  linux-base                                            4.0ubuntu1                                    all          Linux image base package
ii  linux-firmware                                        1.157.6                                       all          Firmware for Linux kernel drivers
ii  linux-generic                                         4.4.0.59.62                                   amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-106                              3.13.0-106.153                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-106-generic                      3.13.0-106.153                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-24                               3.13.0-24.47                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                       3.13.0-24.47                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-29                               3.13.0-29.53                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                       3.13.0-29.53                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                  all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                  amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                 all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                 amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-57                                4.4.0-57.78                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-57-generic                        4.4.0-57.78                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-59                                4.4.0-59.80                                   all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-59-generic                        4.4.0-59.80                                   amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.4.0.59.62                                   amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-106-generic                        3.13.0-106.153                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-24-generic                         3.13.0-24.47                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-29-generic                         3.13.0-29.53                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                  amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-93-generic                         3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-57-generic                          4.4.0-57.78                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-59-generic                          4.4.0-59.80                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-106-generic                  3.13.0-106.153                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                   3.13.0-24.47                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                   3.13.0-29.53                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                  amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic                   3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-57-generic                    4.4.0-57.78                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-59-generic                    4.4.0-59.80                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                   4.4.0.59.62                                   amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  4.4.0-59.80                                   amd64        Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu5                          all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:6.03+dfsg-11ubuntu1                         all          collection of bootloaders (common)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu8                          amd64        Bootloader for Linux/i386 using MS-DOS floppies
```


awesome it's all going great. What would be the recommended way to install Win 10 alongside this install of Ubuntu.

---

### Post by Bashing-om on 2017-01-14
Mista G Nerd; Kiijs great .. 

Doing well .
I have but one other thing .
let's see if the package manager is now functional to the point of coping with the removal of old kernels:
```

sudo apt autoremove

```

As to installing Win10 . Not have a thing I can advise as I do not do Windows . I am aware however that when Windows is installed it will over write the boot code . Will require that ubunu's boot code be re-installed if both are installed to the same drive .

[INDENT][INDENT]shinning like a 
[INDENT][INDENT][INDENT]Liberty silver dollar
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mista G Nerd on 2017-01-14
sudo apt autoremove
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Bashing-om on 2017-01-14
Mista G Nerd; hummmm ...

Wonder what the story here is that autoremove does not remove the old kernels .
We can manually intervene and remove them and await new kernel installs to pursue this autoremove matter.
what is set for "holding" :
```

apt-mark showauto | grep linux-image
apt-mark showmanual | grep linux-image

``` where what is desired here is a null return from showmanual .

Else: well -> 
What is set at this time for booting :
```

uname -r
ls -al /vmlinuz* /initrd.img*

```
and we have the package manager remove the other kernels from the system.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

