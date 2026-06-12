---
title: "ubuntu software - do not have permission"
date: 2021-01-13
forum: Installation &amp; Upgrades
---

### Post by linerman on 2021-01-13
Hi,

Today I have noticed, that when I am on my page in Ubuntu Software  - "Updates" and click refresh, then I got info:

"Unable to update: you do not have permission to install software"

I have checked my repos. Nothing is changed, I even uncheck some of them. Still nothing.

---

### Post by TheFu on 2021-01-13
Is the userid part of the sudo group?
Use the 'id' command to check that.

---

### Post by linerman on 2021-01-13
Yes, my username is among others in sudo group.

---

### Post by ActionParsnip on 2021-01-13
what is the full output of:
```

sudo apt clean; sudo apt update; sudo apt upgrade

```
Thanks

---

### Post by linerman on 2021-01-13
> **ActionParsnip said:**
> what is the full output of:
```

sudo apt clean; sudo apt update; sudo apt upgrade

```
Thanks

```
Stary:1 http://pl.archive.ubuntu.com/ubuntu focal InRelease
Stary:2 http://ppa.launchpad.net/starws-box/deadbeef-player/ubuntu focal InRelease
Pobieranie:3 http://pl.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Pobieranie:4 http://pl.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Stary:5 http://archive.canonical.com/ubuntu focal InRelease     
Pobieranie:6 http://pl.archive.ubuntu.com/ubuntu focal-security InRelease [109 kB]
Pobieranie:7 http://pl.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [752 kB]
Pobieranie:8 http://pl.archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [404 kB]
Pobieranie:9 http://pl.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [264 kB]
Pobieranie:10 http://pl.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [281 kB]
Pobieranie:11 http://pl.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]
Pobieranie:12 http://pl.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [1&#8239;768 B]
Pobieranie:13 http://pl.archive.ubuntu.com/ubuntu focal-security/main amd64 DEP-11 Metadata [24,3 kB]
Pobieranie:14 http://pl.archive.ubuntu.com/ubuntu focal-security/universe amd64 DEP-11 Metadata [56,6 kB]
Pobrano 2&#8239;110 kB w 1s (2&#8239;622 kB/s)                                            
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Wszystkie pakiety s&#261; aktualne.
Czytanie list pakietów... Gotowe
Budowanie drzewa zale&#380;no&#347;ci       
Odczyt informacji o stanie... Gotowe
Obliczanie aktualizacji... Gotowe
0 aktualizowanych, 0 nowo instalowanych, 0 usuwanych i 0 nieaktualizowanych.

```

problem looks like on screenshot
[[IMG]https://i.ibb.co/30R7dTy/screenshot.jpg[/IMG]]("https://ibb.co/30R7dTy")

---

### Post by TheFu on 2021-01-13
Looks like an **Ubuntu Software** issue to me.  Is that a snap? If so, perhaps changing to the APT version will fix this issue?

BTW, I use **sudo apt full-upgrade** to move up to new kernel versions when possible. It will also replace other software based on dependencies. For a desktop, I'd say full-upgrade is probably more what you'd prefer.  Of course, ensure you always have backups before any updates - or create a file system snapshot at least, so you can revert to the pre-update files. Snapshots like this require using LVM or ZFS or perhaps BTRFS, but I don't know about that last one.

---

### Post by linerman on 2021-01-19
I guess it was a problem with system-updates. After few days new updates came out. Now , everything is back to normal without any intervention.

---

