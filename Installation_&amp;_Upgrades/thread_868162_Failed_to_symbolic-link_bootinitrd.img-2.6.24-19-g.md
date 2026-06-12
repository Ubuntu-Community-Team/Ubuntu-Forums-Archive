---
title: "Failed to symbolic-link /boot/initrd.img-2.6.24-19-generic to initrd.img."
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by chicogrande on 2008-07-23
Greetings! I have a working Ubuntu installation using instructions found on pendrivelinux.com (used the [Ubuntu 8.04 Live CD instructions]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/"))

My issue is that I recently ran the updater, which appears to be installing a new version of the kernel, etc. and ran into the following issue:

```
Setting up linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs is disabled since running on a live CD
Failed to symbolic-link /boot/initrd.img-2.6.24-19-generic to initrd.img.
dpkg: error processing linux-image-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic; however:
  Package linux-image-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-bin (6-06-0ubuntu1) ...
/usr/lib/jvm/java-6-sun-1.6.0.06/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jdk:
 sun-java6-jdk depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-jdk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 sun-java6-bin
 sun-java6-plugin
 sun-java6-jdk

```

Additionally, I was working on installing the Sun Java JDK, which appears to be failing due to the previous dependency issues.

When I inspect the /boot directory I do **not** have a initrd.img-2.6.24-19-generic file. Not sure why. I can understand why the link would fail, but not sure why I would not have this file nor how I might go about getting it.

I've searched around the forums for others with this issue, and tried a few suggested fixes (like a 'safe-upgrade') to no avail.

Perhaps I'm simply not following upgrade instructions to accommodate a usb type install of Ubuntu?

Any ideas?

---

### Post by kcash on 2008-08-01
I am also having this problem. Any help would be greatly appreciated.

---

### Post by danzvash on 2008-08-01
Also have this issue. Pretty sure the line
```
update-initramfs is disabled since running on a live CD
```
is the clue here.
Still looking for a workaround - but at least it doesn't prevent other installs.

---

