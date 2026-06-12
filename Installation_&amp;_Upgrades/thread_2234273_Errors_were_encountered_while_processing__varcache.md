---
title: "Errors were encountered while processing:  /var/cache/apt/archives/gnome-settings-dae"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by mituss on 2014-07-13
pls someone can help with this problem
```

Errors were encountered while processing:
 /var/cache/apt/archives/gnome-settings-daemon_3.8.99+git20140121172643~beaa438856_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-settings-daemon udev
Suggested packages:
  gnome-screensaver
The following NEW packages will be installed:
  gnome-settings-daemon
The following packages will be upgraded:
  udev
1 upgraded, 1 newly installed, 0 to remove and 70 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1.711 kB of archives.
After this operation, 6.163 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up libudev1:amd64 (204-5ubuntu20.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
(Reading database ... 235402 files and directories currently installed.)
Preparing to unpack .../udev_204-5ubuntu20.2_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.2) over (204-5ubuntu20) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.6.7.1-1) ...
Setting up udev (204-5ubuntu20.2) ...
udev stop/waiting
udev start/running, process 7529
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-30-generic
(Reading database ... 235402 files and directories currently installed.)
Preparing to unpack .../gnome-settings-daemon_3.8.99+git20140121172643~beaa438856_amd64.deb ...
Unpacking gnome-settings-daemon (3.8.99+git20140121172643~beaa438856) ...
dpkg: error processing archive /var/cache/apt/archives/gnome-settings-daemon_3.8.99+git20140121172643~beaa438856_amd64.deb (--unpack):
 trying to overwrite '/usr/share/GConf/gsettings/gnome-settings-daemon.convert', which is also in package gnome-settings-daemon-schemas 3.8.6.1-0ubuntu11
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-settings-daemon_3.8.99+git20140121172643~beaa438856_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

