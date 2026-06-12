---
title: "Remove packages from the &quot;autoremove&quot; list"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by ehamberg on 2007-01-24
After removing some KDE apps I don't use apt-get suggests to remove a lot of necessary packages every time I use it:

```
The following packages were automatically installed and are no longer required:
  libpopt-dev liblaunchpad-integration0 libattr1-dev kdelibs4-dev libaspell-dev
  libtunepimp-bin libtasn1-3-dev libgpg-error-dev kpackage libpcre3-dev libopencdk8-dev
  libgcrypt11-dev kdemultimedia-kappfinder-data ksmserver ksysguard qt3-dev-tools libsasl2-dev
  libavahi-client-dev libjasper-1.701-dev mpeglib libpcrecpp0 libavahi-qt3-dev libacl1-dev
  libgnutls-dev libqt3-mt-dev ksysv hspell kuser libdbus-1-dev libxslt1-dev libarts1-mpeglib
  libtiff4-dev libart-2.0-dev liblzo-dev libqt3-headers libtiffxx0c2 kpersonalizer
  libtotem-plparser1 kdelibs libxml2-utils kappfinder libopenexr-dev karm kate secpolicy
  libavahi-common-dev libnautilus-extension1 kdesdk-scripts libcupsys2-dev libgnome-desktop-2
  gettext-kde libarts1-xine libidn11-dev libbz2-dev libarts1-dev

```

How can I "remove" them from that list?

---

### Post by JamieC on 2007-01-24
Open a terminal and type the following:
```

sudo apt-get autoremove

```

Are you sure they are no longer required, though?

---

### Post by Pobega on 2007-01-24
If apt is telling you that you have to use autoremove to remove them, then they're not being used by anything else, so it's safe to remove them.

---

### Post by JamieC on 2007-01-24
> **Pobega said:**
> If apt is telling you that you have to use autoremove to remove them, then they're not being used by anything else, so it's safe to remove them.

Granted, but I have seen instances where it wrongly reported packages which were safe to remove.

---

### Post by Pobega on 2007-01-24
> **JamieC said:**
> Granted, but I have seen instances where it wrongly reported packages which were safe to remove.

I suppose if you downloaded something from source and didn't register it in apt it may do that, but you can always just reinstall the library as a standalone package.

---

