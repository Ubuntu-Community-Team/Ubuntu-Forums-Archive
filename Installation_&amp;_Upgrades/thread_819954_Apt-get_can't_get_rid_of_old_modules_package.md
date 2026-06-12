---
title: "Apt-get can't get rid of old modules package"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2008-06-05
Hi,

I was just removing old kernels as I was running out of disk on /boot, and something broke with the 2.6.22-14-generic one, and now my apt is broken. I've tried pretty much everything and am at the end of my rope with it now... here's the error:

```

eneva@manticore:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 9 not upgraded.
1 not fully installed or removed.
After this operation, 9843kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 231368 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So, the 2.6.22-14 files don't really anymore exist on /boot but for some reason apt thinks they should be there. I've tried --remove, --purge, with -f... nothing works.. :(

---

### Post by kaibob on 2008-06-05
I had a somewhat similar problem and the solution was to create an empty directory as follows:

/lib/modules/2.6.22-14-generic

This doesn't work for everyone, but it only takes a minute or so to give it a try.

---

### Post by iaculallad on 2008-06-05
Open /var/lib/dpkg/status file and remove any reference to your linux-ubuntu-modules-2.6.22-14-generic. Save the file and redo any update.

```
sudo gedit /var/lib/dpkg/status
```

---

