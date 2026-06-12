---
title: "Update Manager error"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by BoojiBoy on 2007-09-02
When I try to update Ubuntu with the Update Manager or apt-get, I get a 'parse error' (see below). Can anyone help? Thank you!

```

adin@linux-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  acpi-support cpp cpp-4.1 gcc gcc-4.1 gcc-4.1-base gij gnome-icon-theme
  gstreamer0.10-plugins-ugly gtk2-engines-pixbuf hal hal-device-manager
  hotkey-setup kdebase-bin kdebase-kio-plugins kdesktop libgcj-bc
  libgcj-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libhal-storage1
  libhal1 libkonq4 libvolume-id0 nautilus-sendto powermanagement-interface
  python-qt3 shared-mime-info udev volumeid
31 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/20.6MB of archives.
After unpacking 995kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
dpkg: parse error, in file `/var/lib/dpkg/available' near line 12975 package `xinit':
 `Replaces' field, syntax error after reference to package `xorg-common'
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Pumalite on 2007-09-02
[https://answers.launchpad.net/ubuntu/+question/10265](https://answers.launchpad.net/ubuntu/+question/10265)

---

### Post by BoojiBoy on 2007-09-05
thanks, that worked!

---

### Post by Pumalite on 2007-09-05
Great! You are welcome.

---

