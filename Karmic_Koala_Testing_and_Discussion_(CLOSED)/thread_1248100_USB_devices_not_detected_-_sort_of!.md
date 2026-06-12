---
title: "USB devices not detected - sort of!"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tchoklat on 2009-08-23
After a recent apt-get upgrade yesterday my HP printer and Powerware UPS are not 'seen' when I try to install them. They are seen with the lsusb command but not by the installation routines for the devises. Any ideas?

tony@tony-desktop:~$ lsusb
Bus 002 Device 004: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 003: ID 03f0:0324 Hewlett-Packard 
Bus 002 Device 002: ID 0592:0002 Powerware Corp. UPS (X-Slot)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0990 Logitech, Inc. QuickCam Pro 9000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


tony

---

### Post by psyke83 on 2009-08-23
The problem: you performed a partial upgrade recently which removed foomatic-db-hpijs (which provides HP printer compatibility).

The solution: re-install the package when it becomes available (i.e., built and installable from the repository).

The morale of the story: don't do partial upgrades without checking if packages are supposed to be removed.

;)

This [recent thread]("http://ubuntuforums.org/showthread.php?t=1228048") discusses partial upgrades in a little more depth.

---

### Post by taavikko on 2009-08-24
> **psyke83 said:**
> The problem: you performed a partial upgrade recently which removed foomatic-db-hpijs (which provides HP printer compatibility).

The solution: re-install the package when it becomes available (i.e., built and installable from the repository).


Not quite because of partial upgrade, since the ubuntu-meta packages has this change
```
ubuntu-meta (1.161) karmic; urgency=low

  * Refreshed dependencies
  * Added ttf-dejavu-core to desktop
  * Removed foomatic-db-hpijs from desktop-recommends
  * Removed ttf-dejavu from desktop

```

---

### Post by psyke83 on 2009-08-24
> **taavikko said:**
> Not quite because of partial upgrade, since the ubuntu-meta packages has this change
```
ubuntu-meta (1.161) karmic; urgency=low

  * Refreshed dependencies
  * Added ttf-dejavu-core to desktop
  * Removed foomatic-db-hpijs from desktop-recommends
  * Removed ttf-dejavu from desktop

```

Interesting... I wonder why they demoted this package? Perhaps the HP drivers are being reorganized into another foomatic package?

---

### Post by taavikko on 2009-08-24
> **psyke83 said:**
> Interesting... I wonder why they demoted this package? Perhaps the HP drivers are being reorganized into another foomatic package?

Found this, ```
foomatic-db (20090819-0ubuntu1) karmic; urgency=low

  * New upstream release
<- SNIP ->
     - Added new driver entries "hpijs-pcl3", "hpijs-pcl5e", and "hpijs-pcl5c",
       to generate PPD files for all non-HP printers being used with HPIJS,
       as HPLIP does not provide PPDs for non-HP printers and foomatic-db-hpijs
       makes HPIJS support for non-HP printers too complicated. Updated
       recommended drivers for all affected printers.
```

---

