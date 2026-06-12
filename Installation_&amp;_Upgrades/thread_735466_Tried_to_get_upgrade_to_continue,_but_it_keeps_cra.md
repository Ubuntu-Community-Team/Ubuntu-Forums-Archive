---
title: "Tried to get upgrade to continue, but it keeps crashing."
date: 2008-03-25
forum: Installation &amp; Upgrades
---

### Post by DayOldPorridge on 2008-03-25
Here's the last few lines before dpkg exits:

```

dpkg: error processing gstreamer0.10-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
Aborted (core dumped)

```

What should I do now?  :/

---

### Post by zvacet on 2008-03-25
```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

---

### Post by DayOldPorridge on 2008-03-25
> **zvacet said:**
> ```
sudo dpkg --configure -a
```

```
sudo apt-get -f install
```

Now it says this, and then exits:

```

Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 122630 files and directories currently installed.)
Preparing to replace hal 0.5.11~rc2-1ubuntu3 (using .../hal_0.5.11~rc2-1ubuntu4_i386.deb) ...
invoke-rc.d: initscript hal, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
invoke-rc.d: initscript hal, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-03-25
sudo apt-clean
sudo apt-get update
sudo apt-get upgrade

---

### Post by DayOldPorridge on 2008-03-25
> **Pumalite said:**
> sudo apt-clean
sudo apt-get update
sudo apt-get upgrade

Same thing happens:

```
dpkg: error processing /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
invoke-rc.d: initscript hal, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Preparing to replace findutils 4.2.31-1ubuntu2.1 (using .../findutils_4.2.32-1ubuntu1_i386.deb) ...
Unpacking replacement findutils ...
Errors were encountered while processing:
 /var/cache/apt/archives/hal_0.5.11~rc2-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Pumalite on 2008-03-25
Sorry:
sudo apt clean

---

### Post by DayOldPorridge on 2008-03-25
> **Pumalite said:**
> Sorry:
sudo apt clean

Doesn't work, but the one I did was sudo apt-get clean.

EDIT: Trying aptitude clean and then upgrade now.  I imagine it's going to have the same result, though.

Well, at least most things finished installing, by the looks of it.  However, I get this at the end:

```

Errors were encountered while processing:
 dbus
 hal
 dhcdbd
 openoffice.org-writer2latex
 policykit

```

---

