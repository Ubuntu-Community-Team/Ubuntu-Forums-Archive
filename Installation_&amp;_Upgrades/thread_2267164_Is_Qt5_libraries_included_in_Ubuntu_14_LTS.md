---
title: "Is Qt5 libraries included in Ubuntu 14 LTS?"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by ocgltd on 2015-02-27
Are the Qt5 libraries included by default with Ubuntu 14 LTS, server edition?  If not, what package(s) need to be added to support apps that need Qt5?

---

### Post by v3.xx on 2015-02-27
This what you mean?

[http://packages.ubuntu.com/trusty/qt5-default](http://packages.ubuntu.com/trusty/qt5-default)

If you add Qt apps through the ubuntu repositories the necessary Qt packages will auto load.

If installing third party apps, you will usually get a list of missing packages during the install process.

What do you want to install?

---

### Post by ocgltd on 2015-02-27
Sorry if this is obvious (I'm new to Ubuntu) but is this in main/universe/multiverse repos?  I can't figure out where it would be added from.

- or - is the a command that will tell me that?

---

### Post by v3.xx on 2015-02-27
You can check package status with:
```
apt-cache policy qt5-default
```
It can be installed by:
```
sudo apt-get install qt5-default
```

---

### Post by tgalati4 on 2015-02-27
```
apt-cache search qt5
```

To find all the qt5-related packages.

```
apt-cache depends qt5-default
```

To find all the dependencies that come with qt5-default.

---

