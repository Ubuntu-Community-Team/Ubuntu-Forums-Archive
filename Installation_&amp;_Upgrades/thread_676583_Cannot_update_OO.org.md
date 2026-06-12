---
title: "Cannot update OO.org"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2008-01-23
Attempted to update from Feisty to Gutsy via package manager, get the following:

This occurs when I attempt to fix the broken packages.

```
E: /var/cache/apt/archives/openoffice.org-writer_1%3a2.3.0-1ubuntu5.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libswui680li.so')
E: /var/cache/apt/archives/openoffice.org-base_1%3a2.3.0-1ubuntu5.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libdbu680li.so')
E: /var/cache/apt/archives/openoffice.org-java-common_1%3a2.3.0-1ubuntu5.3_all.deb: conflicting packages - not installing openoffice.org-java-common
E: /var/cache/apt/archives/openoffice.org-core_1%3a2.3.0-1ubuntu5.3_i386.deb: conflicting packages - not installing openoffice.org-core


```

I am afraid to restart my computer for fear of something not working.

---

### Post by VoiceOvGod on 2008-01-23
Update:

```
E: /var/cache/apt/archives/openoffice.org-writer_1%3a2.3.0-1ubuntu5.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libswui680li.so')
E: /var/cache/apt/archives/openoffice.org-base_1%3a2.3.0-1ubuntu5.3_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libdbu680li.so')
```

Looks like Writer and Base are the ones that don't work.

---

### Post by ryanVickers on 2008-01-23
could you look in Synaptic under the "Broken" category, and try a "re-install"?

---

### Post by VoiceOvGod on 2008-01-23
Looks like the local cache was broken.

Found where to clear the cache.

Now I just gotta figure out how to get the little icons back in my menus.

---

### Post by ryanVickers on 2008-01-23
There is an option in gTweakUI to enable/Disable the icons, but I would imagine that if you logoff and back on it should do the trick ;D

---

### Post by VoiceOvGod on 2008-01-23
Just tried that.

No luck.

I attached a screenshot.

Note the lack of icons, and the lack of the _ [] X in the upper right window corner.

---

### Post by ryanVickers on 2008-01-24
It looks like the whole gconf is shot... keys for storing where the icons are and buttons are all in there...

Run "gconf-editor" and see if there are any keys - pray there are, or you'll be switching to KDE... or a new install... :(

---

### Post by VoiceOvGod on 2008-01-24
ok, I got the editor open, where would I find the keys?

---

