---
title: "Crash Report"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by JustAnotherVagueAnon on 2008-06-17
Upon trying to install the new kernel (.19, I think), I got an error because /BOOT was full. I used synaptic to try to remove an older kernel and it said it could not be completely removed. Now when I try to update, I get an error saying a crash occured. Here is the full output.

```

bbraun@bbraun-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-17-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 17.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146818 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by iaculallad on 2008-06-17
Try installing util-linux then retry your update:

```
sudo apt-get install util-linux
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by JustAnotherVagueAnon on 2008-06-17
"util-linux is already the newest version"

Every time I attempt to remove linux-ubuntu-modules-2.6.24-17-generic, I get a crash report and am unable to remove it.

---

### Post by iaculallad on 2008-06-17
Try removing the postrm scripts that prevented apt from removing these packages.

```
sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-17-generic.postrm
sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-17-generic.postrm

sudo apt-get remove linux-ubuntu-modules-2.6.24-17-generic
sudo apt-get remove linux-backports-modules-2.6.24-17-generic
```

---

