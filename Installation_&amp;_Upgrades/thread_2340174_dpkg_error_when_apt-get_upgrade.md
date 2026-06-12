---
title: "dpkg error when apt-get upgrade"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by bstrawt90 on 2016-10-16
Good Day All!

I am posting this thread because I have recently tried to upgrade my OS: via 

```


apt-get update
apt-get install


```

I then ran into the issue:

```


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic ubuntu-core-launcher
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin gir1.2-dbusmenu-glib-0.4 gnome-calculator
  init init-system-helpers initramfs-tools initramfs-tools-bin initramfs-tools-core kbd
  klibc-utils libappstream-glib8 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libklibc liblightdm-gobject-1-0 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnm0
  liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0 libpam-systemd libsystemd0
  libtracker-sparql-1.0-0 libudev1 lightdm linux-firmware linux-libc-dev network-manager
  oxideqt-codecs systemd systemd-sysv tzdata udev xserver-common xserver-xorg-core
39 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/86.7 MB of archives.
After this operation, 165 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
[U][B]dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-4.4.0-38': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/B][/U]

```

I then tried to clean up stale package data and all ran with success:

```

apt-get clean
apt-get autoclean
apt-get autoremove


```

My current build is:

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

kernel 4.4.0-38-generic


This is also preventing me I believe to create VMs via VirtualBox. When I try to make a VM I get the following issue:
```


 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

as root.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 


```

Any ideas on why I am getting the error when trying to upgrade?

Thanks!
Bryan S

---

