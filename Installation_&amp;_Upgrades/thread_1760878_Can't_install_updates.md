---
title: "Can't install updates"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by p2ranger on 2011-05-17
I'm running Ubuntu 10.04 server. I haven't done any updates to it in a few months, so I tried to do that.

It won't update anything. 

I've tried some suggestions from other posts I've found, but nothing has made a difference. I have also tried deleting 

/var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb

so it would download the file again, but no success

The flag that I'm seeing is that my /boot is full. I don't know how that happened, but it is. I'm afraid to delete anything in there as I don't know what is what in there. I have a feeling this is my problem.

I would appreciate any help. Thanks

This is what it looks like when I try to install updates:

```
jason@lfs:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.32-31-generic but it is not installed
  linux-image-generic-pae: Depends: linux-image-2.6.32-31-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
jason@lfs:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.32-31-generic linux-image-2.6.32-31-generic-pae
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-31-generic linux-image-2.6.32-31-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 122 not upgraded.
6 not fully installed or removed.
Need to get 0B/63.2MB of archives.
After this operation, 199MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 108942 files and directories currently installed.)
Unpacking linux-image-2.6.32-31-generic (from .../linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.32-31-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.32-29-generic-pae
Found kernel: /vmlinuz-2.6.32-29-generic
Found kernel: /vmlinuz-2.6.32-28-generic-pae
Found kernel: /vmlinuz-2.6.32-28-generic
Found kernel: /vmlinuz-2.6.32-27-generic-pae
Found kernel: /vmlinuz-2.6.32-27-generic
Found kernel: /vmlinuz-2.6.32-26-generic-pae
Found kernel: /vmlinuz-2.6.32-26-generic
Found kernel: /vmlinuz-2.6.32-25-generic-pae
Found kernel: /vmlinuz-2.6.32-25-generic
Found kernel: /vmlinuz-2.6.32-24-generic-pae
Found kernel: /vmlinuz-2.6.32-24-generic
Found kernel: /vmlinuz-2.6.31-22-generic-pae
Found kernel: /vmlinuz-2.6.31-22-generic
Found kernel: /vmlinuz-2.6.28-19-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Unpacking linux-image-2.6.32-31-generic-pae (from .../linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.32-31-generic-pae': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.32-29-generic-pae
Found kernel: /vmlinuz-2.6.32-29-generic
Found kernel: /vmlinuz-2.6.32-28-generic-pae
Found kernel: /vmlinuz-2.6.32-28-generic
Found kernel: /vmlinuz-2.6.32-27-generic-pae
Found kernel: /vmlinuz-2.6.32-27-generic
Found kernel: /vmlinuz-2.6.32-26-generic-pae
Found kernel: /vmlinuz-2.6.32-26-generic
Found kernel: /vmlinuz-2.6.32-25-generic-pae
Found kernel: /vmlinuz-2.6.32-25-generic
Found kernel: /vmlinuz-2.6.32-24-generic-pae
Found kernel: /vmlinuz-2.6.32-24-generic
Found kernel: /vmlinuz-2.6.31-22-generic-pae
Found kernel: /vmlinuz-2.6.31-22-generic
Found kernel: /vmlinuz-2.6.28-19-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb
 /var/cache/apt/archives/linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@lfs:~$ 

```

Here is a listing of my /boot:
```
jason@lfs:/boot$ ls -l
total 224982
-rw-r--r-- 1 root root  530366 2010-08-18 17:20 abi-2.6.28-19-server
-rw-r--r-- 1 root root  629853 2010-08-18 20:07 abi-2.6.31-22-generic
-rw-r--r-- 1 root root  633629 2010-08-18 20:23 abi-2.6.31-22-generic-pae
-rw-r--r-- 1 root root  651618 2010-09-16 12:14 abi-2.6.32-24-generic
-rw-r--r-- 1 root root  654985 2010-09-16 12:32 abi-2.6.32-24-generic-pae
-rw-r--r-- 1 root root  651949 2010-10-16 17:46 abi-2.6.32-25-generic
-rw-r--r-- 1 root root  655316 2010-10-16 18:03 abi-2.6.32-25-generic-pae
-rw-r--r-- 1 root root  651949 2010-11-24 06:57 abi-2.6.32-26-generic
-rw-r--r-- 1 root root  655316 2010-11-24 07:17 abi-2.6.32-26-generic-pae
-rw-r--r-- 1 root root  651949 2010-12-01 17:48 abi-2.6.32-27-generic
-rw-r--r-- 1 root root  655316 2010-12-01 17:59 abi-2.6.32-27-generic-pae
-rw-r--r-- 1 root root  651949 2011-01-10 18:18 abi-2.6.32-28-generic
-rw-r--r-- 1 root root  655316 2011-01-10 18:36 abi-2.6.32-28-generic-pae
-rw-r--r-- 1 root root  651949 2011-02-11 12:56 abi-2.6.32-29-generic
-rw-r--r-- 1 root root  655316 2011-02-11 13:07 abi-2.6.32-29-generic-pae
-rw-r--r-- 1 root root   97047 2010-08-18 17:20 config-2.6.28-19-server
-rw-r--r-- 1 root root  111349 2010-08-18 20:07 config-2.6.31-22-generic
-rw-r--r-- 1 root root  111782 2010-08-18 20:23 config-2.6.31-22-generic-pae
-rw-r--r-- 1 root root  115905 2010-09-16 12:14 config-2.6.32-24-generic
-rw-r--r-- 1 root root  116360 2010-09-16 12:32 config-2.6.32-24-generic-pae
-rw-r--r-- 1 root root  116047 2010-10-16 17:46 config-2.6.32-25-generic
-rw-r--r-- 1 root root  116502 2010-10-16 18:03 config-2.6.32-25-generic-pae
-rw-r--r-- 1 root root  116048 2010-11-24 06:57 config-2.6.32-26-generic
-rw-r--r-- 1 root root  116503 2010-11-24 07:17 config-2.6.32-26-generic-pae
-rw-r--r-- 1 root root  116048 2010-12-01 17:48 config-2.6.32-27-generic
-rw-r--r-- 1 root root  116503 2010-12-01 17:59 config-2.6.32-27-generic-pae
-rw-r--r-- 1 root root  116037 2011-01-10 18:18 config-2.6.32-28-generic
-rw-r--r-- 1 root root  116492 2011-01-10 18:36 config-2.6.32-28-generic-pae
-rw-r--r-- 1 root root  116037 2011-02-11 12:56 config-2.6.32-29-generic
-rw-r--r-- 1 root root  116492 2011-02-11 13:07 config-2.6.32-29-generic-pae
drwxr-xr-x 2 root root    1024 2011-05-17 11:49 grub
-rw-r--r-- 1 root root 8070655 2010-09-17 10:32 initrd.img-2.6.28-19-server
-rw-r--r-- 1 root root 7515531 2010-09-16 10:45 initrd.img-2.6.31-22-generic
-rw-r--r-- 1 root root 8298644 2010-09-16 14:24 initrd.img-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 9011395 2010-09-18 06:41 initrd.img-2.6.32-24-generic
-rw-r--r-- 1 root root 8964883 2010-09-18 06:42 initrd.img-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 9011955 2010-10-20 06:49 initrd.img-2.6.32-25-generic
-rw-r--r-- 1 root root 8965848 2010-10-20 06:50 initrd.img-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 9015503 2010-11-30 06:53 initrd.img-2.6.32-26-generic
-rw-r--r-- 1 root root 8965662 2011-01-07 22:22 initrd.img-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 9015774 2011-01-11 06:33 initrd.img-2.6.32-27-generic
-rw-r--r-- 1 root root 8965761 2011-01-20 06:38 initrd.img-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 9015791 2011-02-02 06:45 initrd.img-2.6.32-28-generic
-rw-r--r-- 1 root root 8965096 2011-03-01 07:25 initrd.img-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 9015198 2011-03-02 06:27 initrd.img-2.6.32-29-generic
-rw-r--r-- 1 root root 8965953 2011-03-02 06:28 initrd.img-2.6.32-29-generic-pae
drwxr-xr-x 2 root root   12288 2010-02-22 07:41 lost+found
-rw-r--r-- 1 root root  160280 2010-03-23 03:37 memtest86+.bin
-rw-r--r-- 1 root root 1472453 2010-08-18 17:20 System.map-2.6.28-19-server
-rw-r--r-- 1 root root 1668337 2010-08-18 20:07 System.map-2.6.31-22-generic
-rw-r--r-- 1 root root 1695708 2010-08-18 20:23 System.map-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 1689036 2010-09-16 12:14 System.map-2.6.32-24-generic
-rw-r--r-- 1 root root 1730172 2010-09-16 12:32 System.map-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 1689915 2010-10-16 17:46 System.map-2.6.32-25-generic
-rw-r--r-- 1 root root 1730990 2010-10-16 18:03 System.map-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 1690205 2010-11-24 06:57 System.map-2.6.32-26-generic
-rw-r--r-- 1 root root 1731307 2010-11-24 07:17 System.map-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 1690473 2010-12-01 17:48 System.map-2.6.32-27-generic
-rw-r--r-- 1 root root 1731577 2010-12-01 17:59 System.map-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 1691056 2011-01-10 18:18 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 1732138 2011-01-10 18:36 System.map-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 1691218 2011-02-11 12:56 System.map-2.6.32-29-generic
-rw-r--r-- 1 root root 1732300 2011-02-11 13:07 System.map-2.6.32-29-generic-pae
-rw-r--r-- 1 root root    1073 2010-08-18 17:22 vmcoreinfo-2.6.28-19-server
-rw-r--r-- 1 root root    1196 2010-08-18 20:09 vmcoreinfo-2.6.31-22-generic
-rw-r--r-- 1 root root    1200 2010-08-18 20:25 vmcoreinfo-2.6.31-22-generic-pae
-rw-r--r-- 1 root root    1196 2010-09-16 12:16 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root    1200 2010-09-16 12:34 vmcoreinfo-2.6.32-24-generic-pae
-rw-r--r-- 1 root root    1196 2010-10-16 17:47 vmcoreinfo-2.6.32-25-generic
-rw-r--r-- 1 root root    1200 2010-10-16 18:05 vmcoreinfo-2.6.32-25-generic-pae
-rw-r--r-- 1 root root    1196 2010-11-24 07:00 vmcoreinfo-2.6.32-26-generic
-rw-r--r-- 1 root root    1200 2010-11-24 07:20 vmcoreinfo-2.6.32-26-generic-pae
-rw-r--r-- 1 root root    1196 2010-12-01 17:50 vmcoreinfo-2.6.32-27-generic
-rw-r--r-- 1 root root    1200 2010-12-01 18:01 vmcoreinfo-2.6.32-27-generic-pae
-rw-r--r-- 1 root root    1196 2011-01-10 18:20 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root    1200 2011-01-10 18:38 vmcoreinfo-2.6.32-28-generic-pae
-rw-r--r-- 1 root root    1196 2011-02-11 12:57 vmcoreinfo-2.6.32-29-generic
-rw-r--r-- 1 root root    1200 2011-02-11 13:08 vmcoreinfo-2.6.32-29-generic-pae
-rw-r--r-- 1 root root 3541328 2010-08-18 17:20 vmlinuz-2.6.28-19-server
-rw-r--r-- 1 root root 3901888 2010-08-18 20:07 vmlinuz-2.6.31-22-generic
-rw-r--r-- 1 root root 3971296 2010-08-18 20:23 vmlinuz-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 4034976 2010-09-16 12:14 vmlinuz-2.6.32-24-generic
-rw-r--r-- 1 root root 4167840 2010-09-16 12:32 vmlinuz-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 4037088 2010-10-16 17:46 vmlinuz-2.6.32-25-generic
-rw-r--r-- 1 root root 4167200 2010-10-16 18:03 vmlinuz-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 4037888 2010-11-24 06:57 vmlinuz-2.6.32-26-generic
-rw-r--r-- 1 root root 4168896 2010-11-24 07:17 vmlinuz-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 4038016 2010-12-01 17:48 vmlinuz-2.6.32-27-generic
-rw-r--r-- 1 root root 4169824 2010-12-01 17:59 vmlinuz-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 4040288 2011-01-10 18:18 vmlinuz-2.6.32-28-generic
-rw-r--r-- 1 root root 4172992 2011-01-10 18:36 vmlinuz-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 4040832 2011-02-11 12:56 vmlinuz-2.6.32-29-generic
-rw-r--r-- 1 root root 4173024 2011-02-11 13:07 vmlinuz-2.6.32-29-generic-pae

```

---

### Post by wildmanne39 on 2011-05-17
> **p2ranger said:**
> I'm running Ubuntu 10.04 server. I haven't done any updates to it in a few months, so I tried to do that.

It won't update anything. 

I've tried some suggestions from other posts I've found, but nothing has made a difference. I have also tried deleting 

/var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb

so it would download the file again, but no success

The flag that I'm seeing is that my /boot is full. I don't know how that happened, but it is. I'm afraid to delete anything in there as I don't know what is what in there. I have a feeling this is my problem.

I would appreciate any help. Thanks

This is what it looks like when I try to install updates:

```
jason@lfs:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.32-31-generic but it is not installed
  linux-image-generic-pae: Depends: linux-image-2.6.32-31-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.
jason@lfs:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.32-31-generic linux-image-2.6.32-31-generic-pae
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.32-31-generic linux-image-2.6.32-31-generic-pae
0 upgraded, 2 newly installed, 0 to remove and 122 not upgraded.
6 not fully installed or removed.
Need to get 0B/63.2MB of archives.
After this operation, 199MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 108942 files and directories currently installed.)
Unpacking linux-image-2.6.32-31-generic (from .../linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.32-31-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.32-29-generic-pae
Found kernel: /vmlinuz-2.6.32-29-generic
Found kernel: /vmlinuz-2.6.32-28-generic-pae
Found kernel: /vmlinuz-2.6.32-28-generic
Found kernel: /vmlinuz-2.6.32-27-generic-pae
Found kernel: /vmlinuz-2.6.32-27-generic
Found kernel: /vmlinuz-2.6.32-26-generic-pae
Found kernel: /vmlinuz-2.6.32-26-generic
Found kernel: /vmlinuz-2.6.32-25-generic-pae
Found kernel: /vmlinuz-2.6.32-25-generic
Found kernel: /vmlinuz-2.6.32-24-generic-pae
Found kernel: /vmlinuz-2.6.32-24-generic
Found kernel: /vmlinuz-2.6.31-22-generic-pae
Found kernel: /vmlinuz-2.6.31-22-generic
Found kernel: /vmlinuz-2.6.28-19-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Unpacking linux-image-2.6.32-31-generic-pae (from .../linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/vmlinuz-2.6.32-31-generic-pae': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.32-29-generic-pae
Found kernel: /vmlinuz-2.6.32-29-generic
Found kernel: /vmlinuz-2.6.32-28-generic-pae
Found kernel: /vmlinuz-2.6.32-28-generic
Found kernel: /vmlinuz-2.6.32-27-generic-pae
Found kernel: /vmlinuz-2.6.32-27-generic
Found kernel: /vmlinuz-2.6.32-26-generic-pae
Found kernel: /vmlinuz-2.6.32-26-generic
Found kernel: /vmlinuz-2.6.32-25-generic-pae
Found kernel: /vmlinuz-2.6.32-25-generic
Found kernel: /vmlinuz-2.6.32-24-generic-pae
Found kernel: /vmlinuz-2.6.32-24-generic
Found kernel: /vmlinuz-2.6.31-22-generic-pae
Found kernel: /vmlinuz-2.6.31-22-generic
Found kernel: /vmlinuz-2.6.28-19-server
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb
 /var/cache/apt/archives/linux-image-2.6.32-31-generic-pae_2.6.32-31.61_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@lfs:~$ 

```

Here is a listing of my /boot:
```
jason@lfs:/boot$ ls -l
total 224982
-rw-r--r-- 1 root root  530366 2010-08-18 17:20 abi-2.6.28-19-server
-rw-r--r-- 1 root root  629853 2010-08-18 20:07 abi-2.6.31-22-generic
-rw-r--r-- 1 root root  633629 2010-08-18 20:23 abi-2.6.31-22-generic-pae
-rw-r--r-- 1 root root  651618 2010-09-16 12:14 abi-2.6.32-24-generic
-rw-r--r-- 1 root root  654985 2010-09-16 12:32 abi-2.6.32-24-generic-pae
-rw-r--r-- 1 root root  651949 2010-10-16 17:46 abi-2.6.32-25-generic
-rw-r--r-- 1 root root  655316 2010-10-16 18:03 abi-2.6.32-25-generic-pae
-rw-r--r-- 1 root root  651949 2010-11-24 06:57 abi-2.6.32-26-generic
-rw-r--r-- 1 root root  655316 2010-11-24 07:17 abi-2.6.32-26-generic-pae
-rw-r--r-- 1 root root  651949 2010-12-01 17:48 abi-2.6.32-27-generic
-rw-r--r-- 1 root root  655316 2010-12-01 17:59 abi-2.6.32-27-generic-pae
-rw-r--r-- 1 root root  651949 2011-01-10 18:18 abi-2.6.32-28-generic
-rw-r--r-- 1 root root  655316 2011-01-10 18:36 abi-2.6.32-28-generic-pae
-rw-r--r-- 1 root root  651949 2011-02-11 12:56 abi-2.6.32-29-generic
-rw-r--r-- 1 root root  655316 2011-02-11 13:07 abi-2.6.32-29-generic-pae
-rw-r--r-- 1 root root   97047 2010-08-18 17:20 config-2.6.28-19-server
-rw-r--r-- 1 root root  111349 2010-08-18 20:07 config-2.6.31-22-generic
-rw-r--r-- 1 root root  111782 2010-08-18 20:23 config-2.6.31-22-generic-pae
-rw-r--r-- 1 root root  115905 2010-09-16 12:14 config-2.6.32-24-generic
-rw-r--r-- 1 root root  116360 2010-09-16 12:32 config-2.6.32-24-generic-pae
-rw-r--r-- 1 root root  116047 2010-10-16 17:46 config-2.6.32-25-generic
-rw-r--r-- 1 root root  116502 2010-10-16 18:03 config-2.6.32-25-generic-pae
-rw-r--r-- 1 root root  116048 2010-11-24 06:57 config-2.6.32-26-generic
-rw-r--r-- 1 root root  116503 2010-11-24 07:17 config-2.6.32-26-generic-pae
-rw-r--r-- 1 root root  116048 2010-12-01 17:48 config-2.6.32-27-generic
-rw-r--r-- 1 root root  116503 2010-12-01 17:59 config-2.6.32-27-generic-pae
-rw-r--r-- 1 root root  116037 2011-01-10 18:18 config-2.6.32-28-generic
-rw-r--r-- 1 root root  116492 2011-01-10 18:36 config-2.6.32-28-generic-pae
-rw-r--r-- 1 root root  116037 2011-02-11 12:56 config-2.6.32-29-generic
-rw-r--r-- 1 root root  116492 2011-02-11 13:07 config-2.6.32-29-generic-pae
drwxr-xr-x 2 root root    1024 2011-05-17 11:49 grub
-rw-r--r-- 1 root root 8070655 2010-09-17 10:32 initrd.img-2.6.28-19-server
-rw-r--r-- 1 root root 7515531 2010-09-16 10:45 initrd.img-2.6.31-22-generic
-rw-r--r-- 1 root root 8298644 2010-09-16 14:24 initrd.img-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 9011395 2010-09-18 06:41 initrd.img-2.6.32-24-generic
-rw-r--r-- 1 root root 8964883 2010-09-18 06:42 initrd.img-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 9011955 2010-10-20 06:49 initrd.img-2.6.32-25-generic
-rw-r--r-- 1 root root 8965848 2010-10-20 06:50 initrd.img-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 9015503 2010-11-30 06:53 initrd.img-2.6.32-26-generic
-rw-r--r-- 1 root root 8965662 2011-01-07 22:22 initrd.img-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 9015774 2011-01-11 06:33 initrd.img-2.6.32-27-generic
-rw-r--r-- 1 root root 8965761 2011-01-20 06:38 initrd.img-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 9015791 2011-02-02 06:45 initrd.img-2.6.32-28-generic
-rw-r--r-- 1 root root 8965096 2011-03-01 07:25 initrd.img-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 9015198 2011-03-02 06:27 initrd.img-2.6.32-29-generic
-rw-r--r-- 1 root root 8965953 2011-03-02 06:28 initrd.img-2.6.32-29-generic-pae
drwxr-xr-x 2 root root   12288 2010-02-22 07:41 lost+found
-rw-r--r-- 1 root root  160280 2010-03-23 03:37 memtest86+.bin
-rw-r--r-- 1 root root 1472453 2010-08-18 17:20 System.map-2.6.28-19-server
-rw-r--r-- 1 root root 1668337 2010-08-18 20:07 System.map-2.6.31-22-generic
-rw-r--r-- 1 root root 1695708 2010-08-18 20:23 System.map-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 1689036 2010-09-16 12:14 System.map-2.6.32-24-generic
-rw-r--r-- 1 root root 1730172 2010-09-16 12:32 System.map-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 1689915 2010-10-16 17:46 System.map-2.6.32-25-generic
-rw-r--r-- 1 root root 1730990 2010-10-16 18:03 System.map-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 1690205 2010-11-24 06:57 System.map-2.6.32-26-generic
-rw-r--r-- 1 root root 1731307 2010-11-24 07:17 System.map-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 1690473 2010-12-01 17:48 System.map-2.6.32-27-generic
-rw-r--r-- 1 root root 1731577 2010-12-01 17:59 System.map-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 1691056 2011-01-10 18:18 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 1732138 2011-01-10 18:36 System.map-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 1691218 2011-02-11 12:56 System.map-2.6.32-29-generic
-rw-r--r-- 1 root root 1732300 2011-02-11 13:07 System.map-2.6.32-29-generic-pae
-rw-r--r-- 1 root root    1073 2010-08-18 17:22 vmcoreinfo-2.6.28-19-server
-rw-r--r-- 1 root root    1196 2010-08-18 20:09 vmcoreinfo-2.6.31-22-generic
-rw-r--r-- 1 root root    1200 2010-08-18 20:25 vmcoreinfo-2.6.31-22-generic-pae
-rw-r--r-- 1 root root    1196 2010-09-16 12:16 vmcoreinfo-2.6.32-24-generic
-rw-r--r-- 1 root root    1200 2010-09-16 12:34 vmcoreinfo-2.6.32-24-generic-pae
-rw-r--r-- 1 root root    1196 2010-10-16 17:47 vmcoreinfo-2.6.32-25-generic
-rw-r--r-- 1 root root    1200 2010-10-16 18:05 vmcoreinfo-2.6.32-25-generic-pae
-rw-r--r-- 1 root root    1196 2010-11-24 07:00 vmcoreinfo-2.6.32-26-generic
-rw-r--r-- 1 root root    1200 2010-11-24 07:20 vmcoreinfo-2.6.32-26-generic-pae
-rw-r--r-- 1 root root    1196 2010-12-01 17:50 vmcoreinfo-2.6.32-27-generic
-rw-r--r-- 1 root root    1200 2010-12-01 18:01 vmcoreinfo-2.6.32-27-generic-pae
-rw-r--r-- 1 root root    1196 2011-01-10 18:20 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root    1200 2011-01-10 18:38 vmcoreinfo-2.6.32-28-generic-pae
-rw-r--r-- 1 root root    1196 2011-02-11 12:57 vmcoreinfo-2.6.32-29-generic
-rw-r--r-- 1 root root    1200 2011-02-11 13:08 vmcoreinfo-2.6.32-29-generic-pae
-rw-r--r-- 1 root root 3541328 2010-08-18 17:20 vmlinuz-2.6.28-19-server
-rw-r--r-- 1 root root 3901888 2010-08-18 20:07 vmlinuz-2.6.31-22-generic
-rw-r--r-- 1 root root 3971296 2010-08-18 20:23 vmlinuz-2.6.31-22-generic-pae
-rw-r--r-- 1 root root 4034976 2010-09-16 12:14 vmlinuz-2.6.32-24-generic
-rw-r--r-- 1 root root 4167840 2010-09-16 12:32 vmlinuz-2.6.32-24-generic-pae
-rw-r--r-- 1 root root 4037088 2010-10-16 17:46 vmlinuz-2.6.32-25-generic
-rw-r--r-- 1 root root 4167200 2010-10-16 18:03 vmlinuz-2.6.32-25-generic-pae
-rw-r--r-- 1 root root 4037888 2010-11-24 06:57 vmlinuz-2.6.32-26-generic
-rw-r--r-- 1 root root 4168896 2010-11-24 07:17 vmlinuz-2.6.32-26-generic-pae
-rw-r--r-- 1 root root 4038016 2010-12-01 17:48 vmlinuz-2.6.32-27-generic
-rw-r--r-- 1 root root 4169824 2010-12-01 17:59 vmlinuz-2.6.32-27-generic-pae
-rw-r--r-- 1 root root 4040288 2011-01-10 18:18 vmlinuz-2.6.32-28-generic
-rw-r--r-- 1 root root 4172992 2011-01-10 18:36 vmlinuz-2.6.32-28-generic-pae
-rw-r--r-- 1 root root 4040832 2011-02-11 12:56 vmlinuz-2.6.32-29-generic
-rw-r--r-- 1 root root 4173024 2011-02-11 13:07 vmlinuz-2.6.32-29-generic-pae

```
Hi type this in a terminal
sudo dpkg --configure -a then
sudo apt-get update and let me know if that worked.:)

---

### Post by Ub11 on 2011-05-17
> **wildmanne39 said:**
> Hi type this in a terminal
sudo dpkg --configure -a then
sudo apt-get update and let me know if that worked.:)

I have a similar problem and when I try that I get 

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: error: failed to open package info file `/var/lib/dpkg/updates/0001' for reading: No such file or directory

However, I also get 

ubuntu@ubuntu:/var/lib/dpkg/updates$ ls -l
total 4
-rw-r--r-- 0 root root 835 2011-05-16 21:51 0001


ubuntu@ubuntu:/var/lib/dpkg/updates$ sudo rm /var/lib/dpkg/updates/*
rm: cannot remove `/var/lib/dpkg/updates/0001': No such file or directory


Please help !

Thanks.

---

### Post by p2ranger on 2011-05-17
Thanks for the suggestion, but that doesn't fix it

Jason

---

### Post by Dutch70 on 2011-05-17
you can try cleaning out your entire system by installing bleachbit. However I've never used a separate /boot since it's not necessary. I think it just complicates things so I'm not sure if it will help.

You can also try running...
```
sudo apt-get -f install
```

and then...
```
sudo apt-get update && sudo apt-get upgrade
```

Edit: Ok, I see you've already tried with -f. 
Why are you using grub legacy instead of grub2?

---

### Post by mörgæs on 2011-05-17
**sudo apt-get clean** and **sudo apt-get autoclean** may free some space.

If you don't solve the problem, you should think of a clean install. Your list shows kernel 2.6.28, which was used in Ubuntu 9.04, and the double upgrade could be the source of the problem.

---

### Post by p2ranger on 2011-05-17
well, i deleted some of those 2.6.28 files and got it to work. Thanks

As to the grub question, I don't know anything about it. That is just what was on there. Should I do something about it?

I'm just wanting to keep current the LTS, not the latest release of ubuntu.

Jason

---

### Post by mörgæs on 2011-05-18
If it works on the old Grub, there is no need to worry, but when you some day switch to a new release, a fresh install would be best. This will also give you Grub 2 automatically in the process.

---

