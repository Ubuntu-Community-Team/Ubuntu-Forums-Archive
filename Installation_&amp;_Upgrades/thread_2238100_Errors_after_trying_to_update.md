---
title: "Errors after trying to update"
date: 2014-08-06
forum: Installation &amp; Upgrades
---

### Post by Ali_Rashed on 2014-08-06
Hey,

I updated earlier today, and since, I've been receiving a ton of errors. I've been trying to troubleshoot, but nothing I've tried seems to be working.

When I run: ```
sudo apt-get install -f
```

This is what it throws back. 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-3.13.0-30-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following packages will be upgraded:
  linux-image-3.13.0-30-generic
1 upgraded, 0 newly installed, 0 to remove and 72 not upgraded.
1 not fully installed or removed.
Need to get 14.6 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-30-generic i386 3.13.0-30.55 [14.6 MB]
Fetched 14.6 MB in 2min 5s (116 kB/s)                                          
(Reading database ... 217916 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-30-generic_3.13.0-30.55_i386.deb ...
Done.
Unpacking linux-image-3.13.0-30-generic (3.13.0-30.55) over (3.13.0-30.54) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-30-generic_3.13.0-30.55_i386.deb (--unpack):
 unable to create `/lib/modules/3.13.0-30-generic/kernel/net/rose/rose.ko.dpkg-new' (while processing `./lib/modules/3.13.0-30-generic/kernel/net/rose/rose.ko'): Input/output error
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-30-generic /boot/vmlinuz-3.13.0-30-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-30-generic_3.13.0-30.55_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any thoughts on what I could try to fix this? I'm running it on VirtualBox, if that's any help.

Thanks!

---

### Post by ian-weisser on 2014-08-06
> **Ali_Rashed said:**
> ```

Unpacking linux-image-3.13.0-30-generic (3.13.0-30.55) over (3.13.0-30.54) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-30-generic_3.13.0-30.55_i386.deb (--unpack):
 unable to create `/lib/modules/3.13.0-30-generic/kernel/net/rose/rose.ko.dpkg-new' (while processing `./lib/modules/3.13.0-30-generic/kernel/net/rose/rose.ko'): **[COLOR=#ff0000]Input/output error[/COLOR]**
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)

```

Do you have enough space on the vdisk?
Does it always fail in the same place?

---

### Post by Ali_Rashed on 2014-08-06
> **ian-weisser said:**
> Do you have enough space on the vdisk?
Does it always fail in the same place?

I should have enough space. It's have ~50% available to use. And yeah, it consistently fails in that same spot.

---

### Post by ian-weisser on 2014-08-06
Is your vdisk partitioned?
Could one partition be full? Or run out of inodes?

---

### Post by Ali_Rashed on 2014-08-06
It's not partitioned, just one 10 GB drive. There's about 4.2 GB free, that should be enough.

---

### Post by ian-weisser on 2014-08-06
If it's not a space issue, could try deleting the offending package so apt will automatically re-download it.
Deleting this package should not affect your system, since it's not installed.
```
sudo rm /var/cache/apt/archives/linux-image-3.13.0-30-generic_3.13.0-30.55_i386.deb
```

---

