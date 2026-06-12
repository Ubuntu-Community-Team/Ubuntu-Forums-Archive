---
title: "how to fix this i get error on trying to install anything or even gnome or unity"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by howhy on 2013-01-13
getting following errors
```
root@UbuntuDesk:~# sudo apt-get install unity
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cups-pk-helper libevolution libmono-addins-gui0.2-cil libcaribou0
  libmono-corlib4.0-cil libcaribou-common libmono-system-security4.0-cil
  gir1.2-upowerglib-1.0 libbonobo2-common libgtkhtml-4.0-common
  libmono-cairo4.0-cil gir1.2-gee-1.0 libmono-system-xml4.0-cil
  libmono-i18n-west4.0-cil gir1.2-telepathyglib-0.12
  libmono-system-drawing4.0-cil cli-common libmono-sharpzip4.84-cil libpst4
  liblaunchpad-integration1.0-cil alacarte bogofilter-bdb libbonobo2-0
  libmono-posix4.0-cil gir1.2-caribou-1.0 libmono-system-core4.0-cil
  libgtkhtml-4.0-0 libmono-system-configuration4.0-cil libmozjs185-1.0
  evolution-common mono-runtime libdbus1.0-cil libmono-addins0.2-cil
  libappindicator0.1-cil gir1.2-folks-0.6 gir1.2-polkit-1.0 gir1.2-gkbd-3.0
  python-gmenu gir1.2-telepathylogger-0.2 gir1.2-gconf-2.0 libgtkspell0
  libgtkhtml-editor-4.0-0 bogofilter-common libgmime2.6-cil mono-4.0-gac gjs
  libdbus-glib1.0-cil mono-gac gir1.2-accountsservice-1.0 libglib2.0-cil
  bogofilter gnome-shell-common libgconf2.0-cil gir1.2-gdesktopenums-3.0
  gir1.2-networkmanager-1.0 liblaunchpad-integration1 libmono-i18n4.0-cil
  gir1.2-gjsdbus-1.0 libgsl0ldbl libgtk2.0-cil gir1.2-panelapplet-4.0 libgjs0c
  libmono-security4.0-cil libgdiplus libmono-system4.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  compiz compiz-gnome compiz-plugins-main-default compizconfig-backend-gconf
  gconf2 libcompizconfig0 libmetacity-private0 metacity-common unity-common
  unity-lens-applications
Suggested packages:
  compizconfig-settings-manager gnome-themes gconf-defaults-service
The following NEW packages will be installed:
  compiz compiz-gnome compiz-plugins-main-default compizconfig-backend-gconf
  gconf2 libcompizconfig0 libmetacity-private0 metacity-common unity
  unity-common unity-lens-applications
0 upgraded, 11 newly installed, 0 to remove and 7 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```

---

### Post by steeldriver on 2013-01-13
> **howhy said:**
> getting following errors
```
[COLOR=Red]root[/COLOR]@UbuntuDesk:~[COLOR=Red]# sudo[/COLOR] apt-get install unity
.
.
.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
```

Are you trying to do this in the recovery console? if so you don't need sudo, but you probably do need to remount the filesystem with read-write permissions:-

```
mount -o remount,rw /
```Note that there is no space between the [FONT=Courier New]remount,rw[/FONT] options

Another possible reason is if you have a GUI package manager running (Synaptic / Software Center)

---

