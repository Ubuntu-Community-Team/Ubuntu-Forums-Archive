---
title: "Upgrading packages past official"
date: 2006-03-01
forum: Installation &amp; Upgrades
---

### Post by jackrabbit123 on 2006-03-01
I'm trying to upgrade the following:
HAL 0.5.7
udev 0.79
dbus 0.60

How do I tell adept or apt-get to install these packages. I've tried downloading them from the repository using 'dpkg -i' to install them.  This claims that hotplug would interfere with udev and won't install it.  However when looking at what's already installed, hotplug and udev are both installed.  I know in gentoo there's a mechanism for unblocking packages. Does a similar mechanism exist in ubuntu?

---

### Post by Xian on 2006-03-01
[QUOTE=jackrabbit123]I'm trying to upgrade the following:
HAL 0.5.7
udev 0.79
dbus 0.60

How do I tell adept or apt-get to install these packages. I've tried downloading them from the repository using 'dpkg -i' to install them.  This claims that hotplug would interfere with udev and won't install it.[/QUOTE]

What repo are you downloading them from? If they are really upgrades then an 'sudo apt-get upgrade' should install them for you automagically. If apt gives you warnings or dependency errors then those first need to be resolved before you override them, because after that point apt will not be functional. Give some examples from the terminal of where you are having problems. There are newer versions of udev that will not work at all with hotplug, and in fact actually conflict with that package. This is probably what has occured in your instance.

---

