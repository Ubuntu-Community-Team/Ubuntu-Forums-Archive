---
title: "[SOLVED] Package Manager -Software Index Broken"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by Poene on 2007-10-04
My package manager broke and I tried fixing it by using this
```
 **peter@peter-desktop:~$ sudo apt-get install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.20-16-generic
Suggested packages:
  linux-doc-2.6.20 linux-source-2.6.20
The following NEW packages will be installed:
  linux-image-2.6.20-16-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/23.1MB of archives.
After unpacking 82.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 101271 files and directories currently installed.)
Unpacking linux-image-2.6.20-16-generic (from .../linux-image-2.6.20-16-generic_2.6.20-16.32_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.32_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!

Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.20-16-generic_2.6.20-16.32_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-desktop:~$ 

```

---

### Post by Poene on 2007-10-04
Forget it. I fixed it by going to Synaptic Package Manager and removing those packages.

---

