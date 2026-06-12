---
title: "Trying to Update linux-image-2.6.12-10-386 via Synaptic..."
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by AlphaMack on 2006-02-18
Using Synaptic package manager to update system components, I tried to update linux-image-2.6.12-10-386 to the latest version and it returns the following error as shown by a dump from using apt-get:

> $ sudo apt-get install linux-image-2.6.12-10-386
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  lilo linux-doc-2.6.12 linux-source-2.6.12
The following packages will be upgraded:
  linux-image-2.6.12-10-386
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.0MB of archives.
After unpacking 0B of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 109924 files and directories currently installed.)
Preparing to replace linux-image-2.6.12-10-386 2.6.12-10.26 (using .../linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb) ...
The directory /lib/modules/2.6.12-10-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.12-10-386 ...
[color=red]dpkg: error processing /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb (--unpack):
 trying to overwrite `/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko', which is also in package ndiswrapper-modules-2.6.12-10-386
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/color]
Searching for GRUB installation directory ... found: /boot/grub .
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.12-10-386_2.6.12-10.28_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

The problem is that I'm afraid of killing ndiswrapper's functionality if I try to do anything.  Suggestions?

---

