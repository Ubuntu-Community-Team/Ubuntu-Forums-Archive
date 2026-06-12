---
title: "Server 8.04, kernel update, dependency problems"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by peerus on 2008-09-10
Hi! Please help me with upgrading Ubuntu Server 8.04 kernel.

Current version 2.6.18-028stab056.1

apt-get update
apt-get upgrade
apt-get dist-upgrade

I try
apt-get install linux-server 

And get following output:

dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-server
 linux-ubuntu-modules-2.6.24-19-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

Is there other way to update kernel? I'm on VPS-hostig and ssh.

Full text:
```
apt-get install linux-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.24-19-server linux-image-server
  linux-ubuntu-modules-2.6.24-19-server
Suggested packages:
  fdutils linux-doc-2.6.24 linux-source-2.6.24
Recommended packages:
  lilo grub
The following NEW packages will be installed:
  linux-image-2.6.24-19-server linux-image-server linux-server
  linux-ubuntu-modules-2.6.24-19-server
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.1MB of archives.
After this operation, 77.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-image-2.6.24-19-server.
(Reading database ... 17471 files and directories currently installed.)
Unpacking linux-image-2.6.24-19-server (from .../linux-image-2.6.24-19-server_2.6.24-19.41_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-19-server.
Unpacking linux-ubuntu-modules-2.6.24-19-server (from .../linux-ubuntu-modules-2.6.24-19-server_2.6.24-19.28_i386.deb) ...
Selecting previously deselected package linux-image-server.
Unpacking linux-image-server (from .../linux-image-server_2.6.24.19.21_i386.deb) ...
Selecting previously deselected package linux-server.
Unpacking linux-server (from .../linux-server_2.6.24.19.21_i386.deb) ...
Setting up linux-image-2.6.24-19-server (2.6.24-19.41) ...
Running depmod.
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/epca.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/nvram.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/cs5535_gpio.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/lp.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/i8k.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/synclink.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/pc8736x_gpio.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/mxser_new.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/generic_serial.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/cyclades.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/scx200_gpio.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/n_r3964.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/dtlk.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/rocket.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/applicom.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/nsc_gpio.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/specialix.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/ppdev.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/synclinkmp.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/synclink_gt.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/hangcheck-timer.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/tlclk.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/sx.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/char/raw.ko: Cannot allocate memory
FATAL: Could not open /lib/modules/2.6.24-19-server/modules.dep.temp for writing: Cannot allocate memory
Failed to run depmod
dpkg: error processing linux-image-2.6.24-19-server (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-server:
 linux-ubuntu-modules-2.6.24-19-server depends on linux-image-2.6.24-19-server; however:
  Package linux-image-2.6.24-19-server is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-2.6.24-19-server; however:
  Package linux-image-2.6.24-19-server is not configured yet.
 linux-image-server depends on linux-ubuntu-modules-2.6.24-19-server; however:
  Package linux-ubuntu-modules-2.6.24-19-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 2.6.24.19.21); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-server
 linux-ubuntu-modules-2.6.24-19-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If i try
apt-get install linux-image-2.6.24-19-server

```

apt-get install linux-image-2.6.24-19-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fdutils linux-doc-2.6.24 linux-source-2.6.24
Recommended packages:
  lilo grub
The following NEW packages will be installed:
  linux-image-2.6.24-19-server
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.5MB of archives.
After this operation, 62.0MB of additional disk space will be used.
Selecting previously deselected package linux-image-2.6.24-19-server.
(Reading database ... 17471 files and directories currently installed.)
Unpacking linux-image-2.6.24-19-server (from .../linux-image-2.6.24-19-server_2.6.24-19.41_i386.deb) ...
Done.
Setting up linux-image-2.6.24-19-server (2.6.24-19.41) ...
Running depmod.
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/cfi_cmdset_0002.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/jedec_probe.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/map_rom.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/cfi_probe.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/map_ram.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/cfi_util.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/chipreg.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/cfi_cmdset_0020.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/cfi_cmdset_0001.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/chips/gen_probe.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/mtdconcat.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/inftl.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/redboot.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/mtd_blkdevs.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/mtdblock_ro.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/rfd_ftl.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/ssfdc.ko: Cannot allocate memory
WARNING: Can't read module /lib/modules/2.6.24-19-server/kernel/drivers/mtd/mtdblock.ko: Cannot allocate memory
FATAL: Could not open /lib/modules/2.6.24-19-server/modules.dep.temp for writing: Cannot allocate memory
Failed to run depmod
dpkg: error processing linux-image-2.6.24-19-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.24-19-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Please, delete this thread [http://ubuntuforums.org/showthread.php?p=5756679](http://ubuntuforums.org/showthread.php?p=5756679)

---

### Post by sygard on 2008-12-16
Did you fix it? I'm having the exact same issue...

---

