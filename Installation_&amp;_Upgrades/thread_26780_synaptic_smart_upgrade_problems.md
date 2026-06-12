---
title: "synaptic smart upgrade problems"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by pixel80r on 2005-04-13
I ran a synaptic smart upgrade from hoary ?? to hoary 5.04 and get I get this error:

E: linux-image-2.6.10-5-386:  subprocess post-installation script returned error exit status 2
E: linux-image-386:  dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.10-5-386:  dependency problems - leaving unconfigured
E: linux-restricted-modules-386:  dependency problems - leaving unconfigured
E: linux-386:  dependency problems - leaving unconfigured

I also tried to execute -  dpkg --configure -a
and get this:

Setting up linux-image-2.6.10-5-386 (2.6.10-34) ...
mkcramfs: ROM image write failed (wrote 2605056 of 4403200 bytes): No space left on device?
Failed to create initrd image.
dpkg: error processing linux-image-2.6.10-5-386 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-386:
 linux-image-386 depends on linux-image-2.6.10-5-386; however:
  Package linux-image-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-image-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.10-5-386:
 linux-restricted-modules-2.6.10-5-386 depends on linux-image-2.6.10-5-386; however:
  Package linux-image-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.10-5-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-386: linux-restricted-modules-386 depends on linux-restricted-modules-2.6.10-5-386; however:
  Package linux-restricted-modules-2.6.10-5-386 is not configured yet.
dpkg: error processing linux-restricted-modules-386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-386:
 linux-386 depends on linux-image-386; however:
  Package linux-image-386 is not configured yet.
 linux-386 depends on linux-restricted-modules-386; however:
  Package linux-restricted-modules-386 is not configured yet.
dpkg: error processing linux-386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.10-5-386
 linux-image-386
 linux-restricted-modules-2.6.10-5-386
 linux-restricted-modules-386
 linux-386


some packages now are not working correctly.

Any idea how to correct this.

---

### Post by Dr Gonzo on 2005-04-13
I believe you are out of hard drive space.```
df -h
```and post what it says.

---

### Post by pixel80r on 2005-04-14
The results of "df -h"
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/hdb3              15G  2.4G   12G  18% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev/hdb1              30M   30M     0 100% /boot
/dev/hdb4              24G  1.2G   21G   6% /home
/dev                   15G  2.4G   12G  18% /.dev
none                  5.0M  2.9M  2.2M  57% /dev
/dev/hdd              589M  589M     0 100% /media/cdrom0
```

I doubt it is a space issue. I have plenty of available drive space left in both my root and home partitions.

Is there any way to repair without hosing the installation?
This is installed on a second hard drive. The primary drive contains windows 2000 pro.

---

