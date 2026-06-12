---
title: "Why does ...?"
date: 2016-06-23
forum: Installation &amp; Upgrades
---

### Post by nashtrik on 2016-06-23
I have noticed that whenever I update my 14.04 after a long time,the installer installs the latest linux image along with old images too. Like today while updating it downloaded linux-image-extra-3.13.0-89-generic which was 36.7 Megs and after that, it downloaded linux-image-extra-3.13.0-86-generic which again was 36.7 Megs. Isn't the updater intelligent enough to discard old version if the new version is available and avoid unnecessary code on my system ?
                                                                        Thanks.

---

### Post by Impavidus on 2016-06-23
The updater should keep the old versions that were already installed and download and install just the latest version. Unless at some earlier stage something went wrong and 3.13.0-86 was marked for installation, but never installed. Maybe```
dpkg --list linux-image\*
``` may shed some light on this.

---

### Post by grahammechanical on 2016-06-23
> Isn't the updater intelligent enough to discard old version if the new  version is available and avoid unnecessary code on my system ?

The updater is intelligent enough not to do that very thing. Imagine. There is an upgrade to the Linux kernel but when you restart you do not load to a working desktop. What do you do now?

I would go to Advanced options for Ubuntu at the Grub boot menu and select the earlier kernel that was working fine before the upgrade and is still present on the system. Then I can load Ubuntu and keep using it until the kernel that broke the OS is itself upgraded by a kernel version that fixes the bug that broke my OS.

In 14.04 I can remove old kernels one at a time by running

```
sudo apt-get autoremove
```

In 16.04 I can remove all kernels except the latest two kernels by running

```
sudo apt autoremove
```

Regards

---

