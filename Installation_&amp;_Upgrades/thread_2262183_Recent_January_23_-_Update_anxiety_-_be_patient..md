---
title: "Recent January 23 - Update anxiety - be patient."
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-01-23
Just updated a whole list but found the following occurred without notification (Using Synaptic)
**Removed the following packages:**
cheese
gir1.2-totem-1.0
gstreamer1.0-clutter
indicator-bluetooth
libcheese-gtk23
libcheese7
libclutter-1.0-0
libclutter-gst-2.0-0
libclutter-gtk-1.0-0
libcogl-pango15
libcogl15
libtotem0
totem
totem-mozilla
unity-control-center
unity-control-center-signon

Got a broken packages warning when I tried to reload the repositories so I hit the fix broken packages.
Was then ablw to re-install the apparently removed packages.

**Installed the following packages:**
gstreamer1.0-clutter (2.0.8-1build1)
indicator-bluetooth (0.0.6+14.04.20140207-0ubuntu2)
libcheese-gtk23 (3.10.2-0ubuntu2)
libcheese7 (3.10.2-0ubuntu2)
libclutter-1.0-0 (1.16.4-0ubuntu2)
libclutter-gst-2.0-0 (2.0.8-1build1)
libclutter-gtk-1.0-0 (1.4.4-3ubuntu2.2)
libcogl-pango15 (1.16.2-1)
libcogl15 (1.16.2-1)
libtotem0 (3.10.1-1ubuntu4)
totem (3.10.1-1ubuntu4)
unity-control-center (14.04.3+14.04.20140922-0ubuntu1)

Something in the new updates caused this, it might be a good idea to check it out.

---

### Post by oceola2 on 2015-01-24
Just a second point: make sure you re-install all the packages that were removed if you do the same thing.
Cheese, gir1.2-totem-1.0, Totem-mozilla and Unity Control Center Signon were also removed and not picked up after fixing the broken
They were re-installed seperately afterthe main group was reinstalled.
One of the reasons for using Synaptic is the regular software updater/installer has no history available for recovery when these things happen.

---

