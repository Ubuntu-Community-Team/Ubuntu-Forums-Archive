---
title: "latest updates want to remove ubuntu-desktop - should I?"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-06-22
See title! (updates from main server.)

Also wants to remove update-notifier and update-manager.

I don't think this is a good idea - have I caught the repos in a half-way house state?

---

### Post by fifth on 2009-06-22
Well Ubuntu desktop is just a meta package, doesn't actually have any apps or libs in it, just dependencies to load the default desktop stuff, so its safe to be removed if you want. Although I wouldn't run the upgrade while its wanting to remove the update packages.

A proper update would not remove the desktop package, so I would hold off for now, sounds like not all packages have been uploaded yet.

You could also try a 'dist-upgrade' to see if that sorts it out.

---

### Post by descendent87 on 2009-06-22
Nope don't do it, it's an update for update-manager-core but wants to remove update-notifier and update-manager.
Just wait and it'll sort itself out eventually

---

### Post by psyke83 on 2009-06-22
*Do not* do this. It should be a prerequisite for users to know how to safely upgrade when testing the development release.

There are [many]("http://ubuntuforums.org/showthread.php?t=1177537") threads like this, take some time to read them.

---

### Post by taavikko on 2009-06-22
Removing ubuntu-desktop package at this stage will leave you cribbled install from what should eventually be karmic 9.10.

After final release removing this package manually isn't such a bad thing to do. (but if intented to eventually upgrade to ubuntu+1, it's one again needed) tricky isn't it :)
Though, it might just be my explanation...

---

### Post by zika on 2009-06-22
plot thickens ... :)

---

### Post by inportb on 2009-06-22
> **taavikko said:**
> Removing ubuntu-desktop package at this stage will leave you cribbled install from what should eventually be karmic 9.10.

After final release removing this package manually isn't such a bad thing to do. (but if intented to eventually upgrade to ubuntu+1, it's one again needed) tricky isn't it :)
Though, it might just be my explanation...

Absolutely. Though there may be no apparent transient effect, the OS would no longer receive changes to the ubuntu-desktop dependencies...

---

### Post by zika on 2009-06-23
Current state at my machine is:```
The following packages have been kept back:
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil 
  libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil 
  mono-2.0-gac mono-gac mono-runtime update-manager-core 
The following NEW packages will be installed:
  libmono-i18n-west2.0-cil{a} libntfs-3g54{a} libsgutils2{a} 
The following packages will be upgraded:
  acpi-support binutils binutils-static evolution evolution-common 
  evolution-documentation-en evolution-plugins evolution-webcal 
  fglrx-modaliases firefox-3.5 firefox-3.5-branding firefox-3.6 
  firefox-3.6-branding gnome-settings-daemon grub-common grub-pc grub2 
  hpijs hplip hplip-cups hplip-data initscripts libelf1 libgpod-common 
  libgpod4 libgsf-1-114 libgsf-1-common libmono-cairo2.0-cil 
  libmono-i18n2.0-cil libmono0 libpango1.0-0 libpango1.0-common 
  libpoppler-glib4 libpoppler5 libsmbclient libusplash0 libwbclient0 
  linux-generic linux-headers-generic linux-image-generic notify-osd 
  ntfs-3g nvidia-180-modaliases poppler-utils python-glade2 python-gtk2 
  samba-common sg3-utils smbclient sudo sysv-rc sysvinit-utils usplash vino 
  xserver-xorg-video-intel xulrunner-1.9.1 xulrunner-1.9.2 
57 packages upgraded, 3 newly installed, 0 to remove and 16 not upgraded.
Need to get 64.2MB of archives. After unpacking 512kB will be used.
Do you want to continue? [Y/n/?] n
```
After I answered "Y" I got to```
The following packages have been kept back:
  libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-data2.0-cil 
  libmono-getoptions2.0-cil libmono-posix2.0-cil libmono-security2.0-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil 
  libmono-system-web2.0-cil libmono-system2.0-cil libmono2.0-cil 
  mono-2.0-gac mono-gac mono-runtime screen update-manager-core 
0 packages upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
``` ... :)

---

### Post by chrisccoulson on 2009-06-23
If you're running on an architecture other than i386, then the update-manager issue is [https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/390751]("https://bugs.edge.launchpad.net/ubuntu/+source/update-manager/+bug/390751")

---

