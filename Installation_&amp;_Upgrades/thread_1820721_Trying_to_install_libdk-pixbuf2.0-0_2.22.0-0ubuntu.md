---
title: "Trying to install libdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.deb..."
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by Wolf_22 on 2011-08-08
I'm running Maverick and I'm trying to install the NDISGTK DEB file (graphical interface for the NDIS wrapper). Each time I do this, it seems to require a dependency... So I played its game and sneaker-netted each deb file (the Wifi is not working on said machine, hence my manual installation of everything in this).

Everything went fine in the installation except for a few files. It first needed the &quot;python-gtk2_2.21.0-0ubuntu1_i386.deb&quot;. So I tried to install it and this asked for the &quot;python-gtk2&quot;. I grabbed it (python-gtk2_2.21.0-0ubuntu1_i386.deb) from the Package Download website, but when I tried to install it, it nagged me for &quot;libgdk-pixbuf2.0-0 (>= 2.21.6)...

Finally, after downloading this too, I tried to install it. Voila! All dependencies passed and I thought I was going for the gold, but right as it began to install, that's when everything bombed:

> dpkg: considering removing libgtk2.0-0 in favour of libgdk-pixbuf2.0-0 ...
dpkg: no, cannot proceed with removal of libgtk2.0-0 (--auto-deconfigure will help):
   libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2)
      libgtk2.0-0 is to be removed.
dpkg: regarding .../libgdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.deb containing libgdk-pixbuf2.0-0: **libgdk-pixbuf2.0-0 conflicts with libgtk2.0-0** (<< 2.21.3)
libgtk2.0-0 (version 2.20.1-0ubuntu2) is present and installed.
dpkg: error processing /home/<computer name>/Documents/libgdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.deb (--install): conflicting packages - not installing libgdk-pixbuf2.0-0
Errors were encountered while processing:
/home/<computer name again>/Documents/libgdk-pixbuf2.0-0_2.22.0-0ubuntu1_i386.debThe part in bold above seems to be the problem here, yes? If so, how on Earth can I go about fixing this? Do I need to uninstall libgtk2.0-0 just to get the NDISGTK to work???

(In case you're wondering, I'm doing all this to get a Wifi adapter to work--which I've done successfully before, but for some reason, I seem to be unable to get it to work this time around and could use some of your guys' excellent advice...)

---

