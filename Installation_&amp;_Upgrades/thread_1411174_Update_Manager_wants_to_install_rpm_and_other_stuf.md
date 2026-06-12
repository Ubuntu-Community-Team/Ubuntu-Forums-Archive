---
title: "Update Manager wants to install rpm and other stuff."
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by Disabled20240622 on 2010-02-19
Reading the list of updates in my UNR 9.10 install I was quite surprised to see a few new installs in the list:

**Distribution updates**
alien
bsd-mailx
build-essential
debhelper
dpkg-dev
fakeroot
html2text
intltool-debian
libmail-sendmail-perl
libqt4-assistant
libqt4-dbus
libqt4-designer
libqt4-gui
libqt4-network
libqt4-opengl
libqt4-script
libqt4-sql
libqt4-sql-sqlite
libqt4-svg
libqt4-xml
libqtcore4
libqtgui4
librpm0
librpmbuild0
librpmio0
libsys-hostname-long-perl
lsb
lsb-core
lsb-cxx
lsb-desktop
lsb-graphics
m4
mailx
ncurses-term
patch
pax
po-debconf
postfix
rpm


This looks wrong to me, what could cause it to push loads of dev/build tools and the redhat package manager on me?

Edit: Unticking these also unticks a "google-chrome-beta" update below. Does this mean they are now dependencies of that package?

---

### Post by gjoellee on 2010-02-19
You can check your software sources in the system menu. If those packages are already installed, this is normal.

---

### Post by Disabled20240622 on 2010-02-19
None of those packages I listed are installed now.

I have all the built in repos selected, plus repos for current wine, current gimp and google chrome.

Google chrome doesn't depend on these "new install" pagages it wants to install, but when I uncheck any of them to update just the stuff I have, it unchecks the google chrome update.

---

### Post by Disabled20240622 on 2010-02-19
It's Google, I'm not quite sure how, but it's either the Google repo itself, or their google-chrome-beta package.

Just going to hash it from my sources for now.

---

### Post by snowpine on 2010-02-19
The Google repository is not a default software source for Ubuntu, and Canonical has no control over its contents or dependencies.

---

### Post by Ranjan_Hegde on 2010-02-19
I have the exact same problem. It is the latest google-chrome-beta. I am not sure why it has dependencies on rpm etc..

sudo apt-get install google-chrome-beta
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  alien bsd-mailx build-essential cvs debhelper dpkg-dev g++ g++-4.4 gettext html2text intltool-debian
  libmail-sendmail-perl libqt3-mt libqt4-assistant libqt4-dbus libqt4-designer libqt4-gui libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml librpm0 librpmbuild0 librpmio0 libstdc++6-4.4-dev
  libsys-hostname-long-perl lsb lsb-core lsb-cxx lsb-desktop lsb-graphics mailx ncurses-term pax po-debconf postfix rpm

---

### Post by howefield on 2010-02-19
> **Ranjan_Hegde said:**
> I have the exact same problem. It is the latest google-chrome-beta. I am not sure why it has dependencies on rpm etc..

[http://code.google.com/p/chromium/issues/detail?id=35639](http://code.google.com/p/chromium/issues/detail?id=35639)

---

