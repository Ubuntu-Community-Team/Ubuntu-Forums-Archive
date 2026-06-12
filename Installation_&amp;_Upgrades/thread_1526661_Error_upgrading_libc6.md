---
title: "Error upgrading libc6"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by OOzypal on 2010-07-08
Hello,

I am getting this error

```
E: /var/cache/apt/archives/libc6_2.11.1-0ubuntu7.2_i386.deb: subprocess new pre-installation script returned error exit status 1
```

What should I do?

---

### Post by OOzypal on 2010-07-08
Opera is giving a hard time to remove

```
 sudo dpkg -r opera
dpkg: error processing opera (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 opera

```

```

sudo dpkg -p opera
Package: opera
Priority: optional
Section: non-free/web
Installed-Size: 32495
Maintainer: Opera Packaging Team <packager@opera.com>
Bugs: https://bugs.opera.com/wizard/
Architecture: i386
Version: 10.60.6386
Provides: www-browser, mail-reader, imap-client, news-reader
Depends: libc6 (>= 2.7-1), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.1.1), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1), libx11-6, libxext6, libxft2 (>> 2.1.1), libxrender1, libxt6, zlib1g (>= 1:1.1.4), gstreamer0.10-plugins-good, libxft2, libxrender1, debconf (>= 0.5) | debconf-2.0
Recommends: ttf-linux-libertine | ttf-freefont | ttf-dejavu | ttf-mscorefonts-installer
Suggests: flashplugin-nonfree, cups-client
Size: 14730770
Description: A fast and secure web browser and Internet suite
 Opera is a small, fast, customizable, powerful and user-friendly web
 browser as well as an Internet suite including an e-mail client, an IRC
 client, web developer tools (Dragonfly) and a personal web server (Opera
 Unite).
Homepage: http://www.opera.com/browser/

```

---

### Post by OOzypal on 2010-07-10
Hello,

Any ideas? Here is what I get when I try to remove opera

```

$ sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages have been kept back:
  opera 
The following packages will be upgraded:
  app-install-data-partner flashplugin-installer kpackagekit libatk1.0-0 libatk1.0-data libc6 libgstfarsight0.10-0 libpam-modules libpam-runtime libpam0g 
  libpng12-0 python-farsight 
The following partially installed packages will be configured:
  byobu gdm libpam-gnome-keyring linux-headers-2.6.32-23-generic linux-headers-generic man-db 
The following packages are RECOMMENDED but will NOT be installed:
  libc6-i686 
12 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/4,427kB of archives. After unpacking 28.7kB will be used.
Do you want to continue? [Y/n/?] 
E: I wasn't able to locate file for the opera package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the opera package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

```

---

