---
title: "kernel won't update"
date: 2016-11-11
forum: Installation &amp; Upgrades
---

### Post by kahzinski on 2016-11-11
hey

I'm trying to ```
sudo apt-get upgrade, sudo apt-get dist-upgrade and sudo apt-get upgrade -f
```, and when I get to the kernel, it fails.


Ubuntu 14.04 (running in VMWare)


Output:


    ```
cody@ubuntu:~$ sudo apt-get upgrade
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    Calculating upgrade... Done
    The following packages were automatically installed and are no longer required:
      fonts-dejavu-extra libcamel-1.2-29 libedataserver-1.2-15 libindicate5
    Use 'apt-get autoremove' to remove them.
    The following packages will be upgraded:
      linux-image-3.13.0-24-generic
    1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    11 not fully installed or removed.
    Need to get 0 B/52.2 MB of archives.
    After this operation, 115 MB of additional disk space will be used.
    Do you want to continue? [Y/n] y
    (Reading database ... 209443 files and directories currently installed.)
    Preparing to unpack .../linux-image-3.13.0-24-generic_3.13.0-24.47~precise2_i386.deb ...
    Done.
    Unpacking linux-image-3.13.0-24-generic (3.13.0-24.47~precise2) over (3.13.0-24.46) ...
    dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-24-generic_3.13.0-24.47~precise2_i386.deb (--unpack):
     trying to overwrite '/lib/modules/3.13.0-24-generic/kernel/sound/i2c/snd-i2c.ko', which is also in package linux-image-extra-3.13.0-24-generic 3.13.0-24.46
    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
    Examining /etc/kernel/postrm.d .
    run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
    run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-24-generic /boot/vmlinuz-3.13.0-24-generic
    Errors were encountered while processing:
     /var/cache/apt/archives/linux-image-3.13.0-24-generic_3.13.0-24.47~precise2_i386.deb
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```



any idea how to fix this?
thanks

---

### Post by ian-weisser on 2016-11-11
> **kahzinski said:**
> Unpacking linux-image-3.13.0-24-generic (3.13.0-24.47~precise2) over (3.13.0-24.46) ...
    dpkg: error processing archive /var/cache/apt/archives/linux-image-3.13.0-24-generic_3.13.0-24.47~precise2_i386.deb (--unpack):
     **trying to overwrite '/lib/modules/3.13.0-24-generic/kernel/sound/i2c/snd-i2c.ko', which is also in package linux-image-extra-3.13.0-24-generic 3.13.0-24.46**
    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)


Why are you trying to install a 12.04 kernel (linux-image-3.13.0-24-generic_3.13.0-24.47~precise2_i386.deb) in a 14.04 system?

Regardless, the problem is clearly that you are trying to install two kernel packages that provide the same files. The two packages *conflict.* You can only install one.

---

