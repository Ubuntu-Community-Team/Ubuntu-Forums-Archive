---
title: "dependency problems after 16.04 upgrade"
date: 2018-07-31
forum: Installation &amp; Upgrades
---

### Post by jocook on 2018-07-31
I upgraded from 14 to 16.04 and have tried; apt-get autoremove  apt-get clean,  apt-get install -f ....etc. Xenial /etc/apt/sources.list looks OK.
There were  unsolved problems with cups service  before upgrade, I hoped may get fixed. I'm now thinking of a complete re-install on this remote machine.
dpkg --configure -a leaves these packages unconfigured;
dbus
 libgirepository-1.0-1:i386
 console-setup
 keyboard-configuration
 initscripts
 console-setup-linux
 cups-daemon
 gir1.2-javascriptcoregtk-4.0:i386
 cryptsetup
 util-linux
 cups
 cups-core-drivers

most messages refer to lsb-base  e.g.
 util-linux depends on lsb-base (>= 4.1+Debian11ubuntu7); however:
  Version of lsb-base on system is 4.1+Debian11ubuntu6.2

apt-cache policy lsb-base
  Installed: 4.1+Debian11ubuntu6.2
  Candidate: 9.20160110ubuntu0.2
  Version table:
     9.20160110ubuntu0.2 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial-updates/main i386 Packages
     9.20160110 0
        500 [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) xenial/main i386 Packages
 *** 4.1+Debian11ubuntu6.2 0
        100 /var/lib/dpkg/status

---

### Post by jocook on 2018-07-31
Don't bother, I've now completely borked the system!
Will reinstall this failed upgrade when someone can be on site.

Unable to delete thread?

---

