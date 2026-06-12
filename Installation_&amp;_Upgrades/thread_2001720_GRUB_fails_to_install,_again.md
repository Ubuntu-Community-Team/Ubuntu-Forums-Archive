---
title: "GRUB fails to install, again"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-06-11
Maybe an uninitialized variable in GRUB leads to random failures to install?  Or could there be some QEMU fault (did this in a VM)?  It was a basic near default install.  I chose UTC time zone and use whole disk w/o LVM.

[http://phil.ipal.org/ubuntu-12.04-server-grub-fail.png](http://phil.ipal.org/ubuntu-12.04-server-grub-fail.png)

I'm re-running it now.

Update:

It looks like a repository issue ...
```
Jun 11 16:29:21 anna[6379]: DEBUG: retrieving grub-installer 1.68ubuntu5
Jun 11 16:29:21 anna[6379]: DEBUG: retrieving grub-mount-udeb 1.99-21ubuntu3
Jun 11 16:35:48 in-target:   iw grub-pc grub-efi-amd64 grub-efi-ia32 grub lilo
Jun 11 16:42:47 in-target:   kernel-patch-badram memtest86 grub-pc grub-legacy mtools spell ssh-askpass
Jun 11 16:47:43 main-menu[304]: INFO: Menu item 'grub-installer' selected
Jun 11 16:47:43 grub-installer: info: architecture: amd64/generic
Jun 11 16:47:49 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:47:49 in-target:   grub-common libfreetype6 os-prober
Jun 11 16:47:50 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:50 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:50 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:47:51 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:47:51 in-target:   grub-common libfreetype6 os-prober
Jun 11 16:47:51 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:52 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:52 in-target: Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:52 in-target: Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:52 in-target: Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:52 in-target: Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:47:53 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:47:54 grub-installer: info: Identified partition label for /dev/sda1: msdos
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-legacy
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-efi
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-efi-amd64-bin
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-efi-amd64
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-efi-ia32-bin
Jun 11 16:47:55 grub-installer: dpkg: warning: there's no installed package matching grub-efi-ia32
Jun 11 16:48:03 in-target:   grub-common grub-gfxpayload-lists grub-pc-bin grub2-common libfreetype6
Jun 11 16:48:03 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:48:03 in-target:   grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
Jun 11 16:48:04 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:48:05 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:48:05 in-target: Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:48:05 in-target: Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:48:05 in-target: Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:48:05 in-target: Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.1 [94.3 kB]
Jun 11 16:48:05 in-target: Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.1 [861 kB]
Jun 11 16:48:08 in-target: Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.1 [140 kB]
Jun 11 16:48:08 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:48:08 grub-installer: info: Calling 'apt-install grub-pc' failed
Jun 11 16:49:43 main-menu[304]: (process:21805): chroot: can't execute 'grub-probe': No such file or directory
Jun 11 16:49:43 main-menu[304]: (process:21805): chroot: can't execute 'grub-probe': No such file or directory
Jun 11 16:49:43 main-menu[304]: WARNING **: Configuring 'grub-installer' failed with error code 1
Jun 11 16:49:43 main-menu[304]: WARNING **: Menu item 'grub-installer' failed.
Jun 11 16:49:56 main-menu[304]: INFO: Menu item 'grub-installer' selected
Jun 11 16:49:56 grub-installer: info: architecture: amd64/generic
Jun 11 16:49:57 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:49:57 in-target:   grub-common libfreetype6 os-prober
Jun 11 16:50:02 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:03 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:50:04 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:50:04 in-target:   grub-common libfreetype6 os-prober
Jun 11 16:50:04 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:05 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:05 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:50:05 grub-installer: info: Identified partition label for /dev/sda1: msdos
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-legacy
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-efi
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-efi-amd64-bin
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-efi-amd64
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-efi-ia32-bin
Jun 11 16:50:05 grub-installer: dpkg: warning: there's no installed package matching grub-efi-ia32
Jun 11 16:50:08 in-target:   grub-common grub-gfxpayload-lists grub-pc-bin grub2-common libfreetype6
Jun 11 16:50:08 in-target:   multiboot-doc grub-emu xorriso desktop-base
Jun 11 16:50:08 in-target:   grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
Jun 11 16:50:08 in-target: Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:09 in-target: Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:09 in-target: Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:09 in-target: Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:09 in-target: Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.1 [2,066 kB]
Jun 11 16:50:09 in-target: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/grub2/grub-common_1.99-21ubuntu3.1_amd64.deb  Hash Sum mismatch
Jun 11 16:50:10 grub-installer: info: Calling 'apt-install grub-pc' failed
Jun 11 16:50:14 main-menu[304]: (process:22190): chroot: can't execute 'grub-probe': No such file or directory
Jun 11 16:50:14 main-menu[304]: (process:22190): chroot: can't execute 'grub-probe': No such file or directory
Jun 11 16:50:14 main-menu[304]: WARNING **: Configuring 'grub-installer' failed with error code 1
Jun 11 16:50:14 main-menu[304]: WARNING **: Menu item 'grub-installer' failed.
```

---

### Post by wilee-nilee on 2012-06-11
Where are you aiming grub at, are you using the something else option and making sure it is the mbr?

Is it a ext4 partitioning setup?

I have not used qemu, but I don't think it is for full installs, not sure though, I use oracles virtualbox.

---

### Post by Skaperen on 2012-06-11
> **wilee-nilee said:**
> Where are you aiming grub at, are you using the something else option and making sure it is the mbr?

Is it a ext4 partitioning setup?

I have not used qemu, but I don't think it is for full installs, not sure though, I use oracles virtualbox.
There was no option to "aim".  It's wherever the installer does it.  The filesystem is whatever the installer chooses when the default "use whole disk" is chosen (I selected the one without LVM).

It has worked many times before.  See my update in my original post.  It seems to be downloading grub packages, getting bad ones, and of course the installer cannot install the bootloader in place if the package isn't installed.

Update:

It appears to be using ext4.

---

### Post by Skaperen on 2012-06-11
It is working now.  It failed three times in a row before this latest test.  It would be nice if someone knew if this was really a bad package file in the repository that was subsequently fixed.

---

