---
title: "apt-get remove catastrophe!"
date: 2014-12-20
forum: Installation &amp; Upgrades
---

### Post by Mark_du_Preez on 2014-12-20
I installed Python 2.7 (already had 3.4) and then didn't need it so I typed "apt-get remove python2.7" and all hell broke loose! Now half of my system is gone!

First of all, WTF!? Why did this happen?

Secondly, is there any way to recover from this disaster?

---

### Post by Bucky Ball on 2014-12-20
If you can open a terminal, try:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Please post back any errors you encounter.

Which release and flavour of Ubuntu are you using? If you have Synaptics installed, then that has an option to 'Fix broken packages'. If not, restart the machine and choose the recovery kernel at boot. The text might give you some clues as to what's going on and eventually you'll get to a screen of options. Choose 'fix broken packages'. Again, report any error messages you encounter. Good luck. ;)

---

### Post by vasa1 on 2014-12-20
> **Mark_du_Preez said:**
> I installed Python 2.7 (already had 3.4) and then didn't need it so I typed "apt-get remove python2.7" and all hell broke loose! Now half of my system is gone!

First of all, WTF!? Why did this happen?
...
Not trying to be funny, but it happened because you allowed it to: AFAIK, "Python2" is still vital to the OS. The transition to "Python3" is far from complete.

If you examined the screen output of "apt-get remove python2.7" you may have had an idea of what was coming your way:```
The following packages will be REMOVED:
  apturl blueman gconf2 gdebi gecko-mediaplayer gksu gnome-mplayer
  gvfs-backends ibus kupfer libgda-5.0-4 libgda-5.0-common libgksu2-0
  libsmbclient light-locker-settings lubuntu-software-center mirage python
  python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-cairo
  python-chardet python-cups python-cupshelpers python-dbus python-debian
  python-defer python-gi python-gnomekeyring python-gobject python-gobject-2
  python-gtk2 python-gudev python-keybinder python-libxml2 python-notify
  python-pkg-resources python-psutil python-pycurl python-pysqlite2 python-six
  python-smbc python-support python-talloc python-xdg python2.7 samba-libs
  system-config-printer-common system-config-printer-gnome transmission-gtk
  ubuntu-release-upgrader-gtk update-manager update-notifier
  update-notifier-common
```

---

### Post by Bucky Ball on 2014-12-20
> **vasa1 said:**
> ```
The following packages will be REMOVED:
  apturl blueman gconf2 gdebi gecko-mediaplayer gksu gnome-mplayer
  gvfs-backends ibus kupfer libgda-5.0-4 libgda-5.0-common libgksu2-0
  libsmbclient light-locker-settings lubuntu-software-center mirage python
  python-apt python-aptdaemon python-aptdaemon.gtk3widgets python-cairo
  python-chardet python-cups python-cupshelpers python-dbus python-debian
  python-defer python-gi python-gnomekeyring python-gobject python-gobject-2
  python-gtk2 python-gudev python-keybinder python-libxml2 python-notify
  python-pkg-resources python-psutil python-pycurl python-pysqlite2 python-six
  python-smbc python-support python-talloc python-xdg python2.7 samba-libs
  system-config-printer-common system-config-printer-gnome transmission-gtk
  ubuntu-release-upgrader-gtk update-manager update-notifier
  update-notifier-common
```

Ouch!

---

