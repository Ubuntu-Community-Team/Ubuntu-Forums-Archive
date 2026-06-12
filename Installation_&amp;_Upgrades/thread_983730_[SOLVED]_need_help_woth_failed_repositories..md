---
title: "[SOLVED] need help woth failed repositories."
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by c/Kr3t on 2008-11-16
after i upgraded from 8.4 lts to 8.10, i always get a notice that some repositories are failed whenever i go to update my system.

this is what shows

```
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

```

i go into my terminal and do apt-cdrom but i'm not sure what i'm supposed to do to fix it.

can anyone help?

---

### Post by inobe on 2008-11-16
are you trying to update with your 8.10 cd ?

you can update online !

---

### Post by c/Kr3t on 2008-11-16
> **inobe said:**
> are you trying to update with your 8.10 cd ?

you can update online !


how do i update it online?  i don't have the cd but i ordered one a while ago just in case

---

### Post by johnn1949 on 2008-11-16
open up system , admin,  software sources.

Uncheck cdrom at the bottom

---

### Post by inobe on 2008-11-16
i am a bit confused, maybe i need another bucket of coffee !

are you currently running version 8.10 ?

if not' are you trying to upgrade to 8.10 from 8.04 ?

-----------------------------------------------------------

---

### Post by c/Kr3t on 2008-11-16
> **johnn1949 said:**
> open up system , admin,  software sources.

Uncheck cdrom at the bottom

i don't have a box to uncheck.  anything else?

---

### Post by johnn1949 on 2008-11-17
system -->administration-->software sources

At the bottom of the window there is a box called "installable from cdrom".  These 2 sources in the box should be unchecked.

If they are already unchecked I don't know.

---

### Post by c/Kr3t on 2009-01-04
that worked,  thanks

---

