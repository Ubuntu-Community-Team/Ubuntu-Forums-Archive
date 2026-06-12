---
title: "[SOLVED] dpkg --configure libpcre3 fails"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by xmarket on 2008-07-21
I did an automatic update on last Friday from gnome: linux-headers(.36), libpcre3(2.1), libpango, evolution stuffs....

The process failed on linux-header, after ~10minutes I did a reset, but normal boot reported a "softlock" stuff, I did a recovery boot and I could run "dpkg --configure -a", which repaired the linux-header..., but pcre3 already failed

now dpkg reports: libpcre3_7.4-1ubuntu2.1: post-installation script: Exec format error (errorcode 2)

az every stuff depending on pcre reports: /usr/lib/libpcre.so.3: file too short

"apt-get install --reinstall libpcre3" doesn't work

any help?

---

### Post by bapoumba on 2008-07-21
> **xmarket said:**
> I did an automatic update on last Friday from gnome: linux-headers(.36), libpcre3(2.1), libpango, evolution stuffs....

The process failed on linux-header, after ~10minutes I did a reset, but normal boot reported a "softlock" stuff, I did a recovery boot and I could run "dpkg --configure -a", which repaired the linux-header..., but pcre3 already failed

now dpkg reports: libpcre3_7.4-1ubuntu2.1: post-installation script: Exec format error (errorcode 2)

az every stuff depending on pcre reports: /usr/lib/libpcre.so.3: file too short

"apt-get install --reinstall libpcre3" doesn't work

any help?
Please try to rename /usr/lib/libpcre.so.3 to something else (do not remove it yet, just in case), and run:
```
sudo apt-get update
sudo apt-get install libpcre3

```

Paste the complete error output, if any.

---

### Post by xmarket on 2008-07-21
I renamed the file to /usr/lib/libpcre3.so.3.orig

The output: (this is a hungarian box[COLOR="Red"]/translations added by me/[/COLOR])


```
Csomaglisták olvasása... [COLOR="Red"]/reading package lists/[/COLOR]
Függ&#337;ségi fa építése... [COLOR="Red"]/dependency tree/[/COLOR]
Állapotinformációk olvasása... [COLOR="Red"]/reading state info/[/COLOR]
libpcre3 már a legújabb verzió. [COLOR="Red"]/libpcre3 is the newest version/[/COLOR]
0 frissített, 0 újonnan telepített, 0 eltávolítandó és 0 nem frissített. [COLOR="Red"]/update, install../[/COLOR]
8 nincs teljesen telepítve/eltávolítva. [COLOR="Red"]/not fully installed.../[/COLOR]
A m&#369;velet végrehajtása után 0B lemezterület kerül felhasználásra. [COLOR="Red"]/will be used/[/COLOR]
Beállítás: libpango1.0-common (1.20.5-0ubuntu1) ... [COLOR="Red"]/Configuring:/[/COLOR]
dpkg (alfolyamat): sikertelen futtatás: post-install script: Exec formátum hiba [COLOR="Red"]/dpkg (subprocess): unable to run: post-install script: Exec format error/[/COLOR]
dpkg: hibás feldolgozás: libpango1.0-common (--configure): [COLOR="Red"]/dpkg: process error/[/COLOR]
 post-installation script alfolyamat 2 hibakóddal kilépett [COLOR="Red"]/subprocess exited by errorcode 2/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: libpango1.0-0: [COLOR="Red"]/unable to configure because of dependency errors/[/COLOR]
 libpango1.0-0 függ&#337;ségek: libpango1.0-common (>= 1.20.5-0ubuntu1); ám: [COLOR="Red"]/dependencies... but/[/COLOR]
  libpango1.0-common csomag még beállítatlan. [COLOR="Red"](package not yet configured)[/COLOR]
dpkg: hibás feldolgozás: libpango1.0-0 (--configure): [COLOR="Red"]/process error/[/COLOR]
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/dependency errors - kept unconfigured/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: libedataserverui1.2-8: [COLOR="Red"]/unable to configure because of dependency errors/[/COLOR]
 libedataserverui1.2-8 függ&#337;ségek: libpango1.0-0 (>= 1.20.1); ám: [COLOR="Red"]/dependencies.../[/COLOR]
  libpango1.0-0 csomag még beállítatlan [COLOR="Red"]/not yet configured/[/COLOR]
dpkg: hibás feldolgozás: libedataserverui1.2-8 (--configure):
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/kept unconfigured/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: libexchange-storage1.2-3: [COLOR="Red"]/unable to configure.../[/COLOR]
 libexchange-storage1.2-3 függ&#337;ségek: libpango1.0-0 (>= 1.20.1); ám:
  libpango1.0-0 csomag még beállítatlan. [COLOR="Red"]/not yet configured/[/COLOR]
dpkg: hibás feldolgozás: lebexchange-storage1.2-3 (--configure):
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/kept unconfigured/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: evolution: [COLOR="Red"]/unable to configure.../[/COLOR]
 evolution függ&#337;ségek: libedataserverui1.2-8 (>= 2.22.2); ám:
  libedataserverui1.2-8 csomag még beállítatlan. [COLOR="Red"]/not yet configured/[/COLOR]
 evolution függ&#337;ségek: libexchange-storage1.2-3 (>= 2.22.2); ám:
  libexchange-storage1.2-3 csomag még beállítatlan.
 evolution függ&#337;ségek: libpango1.0-0 (>= 1.20.1); ám:
  libpango1.0-0 csomag még beállítatlan.
dpkg: hibás feldolgozás: evolution (--configure): [COLOR="Red"]/process error/[/COLOR]
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/kept unconfigured/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: evolution-plugins: [COLOR="Red"]/unable to conf.../[/COLOR]
 evolution-plugins függ&#337;ségek: evolution (2.22.3.1); ám:
  evolution csomag még beálítatlan. [COLOR="Red"]/not yet configured/[/COLOR]
 evolution-plugins függ&#337;ségek: libedataserverui1.2-8 (>= 2.22.2); ám:
  libedataserverui1.2-8 csomag még beállítatlan.
 evolution-plugins függ&#337;ségek: libpango1.0-0 (>= 1.20.1); ám:
  libpango1.0-0 csomag még beállítatlan.
dpkg: hibás feldolgozás: evolution-plugins (--configure):
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/kept unconfigured/[/COLOR]
Beállítás: libpcre3 (7.4-1ubuntu2.1) ... [COLOR="Red"]/Configuring.../[/COLOR]
dpkg (alfolyamat): sikertelen futtatás: post-installation script: Exec formátum hiba [COLOR="Red"]/dpkg (subprocess): unable to run: post-install script: Exec format error/[/COLOR]
dpkg: hibás feldolgozás: libpcre3 (--configure):
 post-installation script alfolyamat 2 hibakóddel kilépett [COLOR="Red"]/subprocess exited by errorcode 2/[/COLOR]
dpkg: függ&#337;ségi gondok miatt nem beállítható e csomag: libpcrecpp0: [COLOR="Red"]/unable to conf.../[/COLOR]
 libpcrecpp0 függ&#337;ségek: libpcre3 (>= 7.4); ám:
  libpcre3 csomag még beállítatlan. [COLOR="Red"]/not yet configured/[/COLOR]
dpkg: hibás feldolgozás: libpcrecpp0 (--configure):
 függ&#337;ségi hibák - e csomag beállítatlan maradt [COLOR="Red"]/kept unconfigured/[/COLOR]
Hibák történetek a feldolgozáskor: [COLOR="Red"]/errors/[/COLOR]
libpango1.0-common
libpango1.0-0
libedataserverui1.2-8
libexchange-storage1.2-3
evolution
evolution-plugins
libpcre3
libpcrecpp0
```

---

### Post by xmarket on 2008-07-21
A few more info:

This is a 8.04.1 box upgraded from 7.10 by update manager(~ a month ago)

```
dpkg --configure -a
```
... had the same output before the rename


There are kinit error messages on boot:
kinit: name_to_dev_t(/dev/disk/by-uuid/{bla-bla}) = sda2(8,2)
kinit: trying to resume from /dev/disk/by-uuid/{same bla-bla}
kinit: No resume image, doing normal boot...


gdm running(there is a stoping line on halt), but I can use the console only

Well, don't know why, but all of hte reported packages were broken.  downloaded them manually from the repo, and installed them by dpkg. Now everythink works as before.... :D

---

### Post by bapoumba on 2008-07-22
I'm very glad to see you got it to work all by yourself :)
Probably the files downloading when the process was interrupted were corrupt (or a corrupt file interrupted the upgrade process). Downloading them again and using dpkg to install was the way to go if only a text-based interface was available. Congrats :)

---

