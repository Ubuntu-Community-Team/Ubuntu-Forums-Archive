---
title: "Can't mount CDRom during install"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by reticulate on 2007-03-29
When installing 6.10 on an older IBM M-Pro install reports "Your CD-ROM could not be mounted. This probably means the CD-ROM is not in the drive........Try to mount the CR-ROM again?" This is after the CD boots and country is selected. Server installs fine.
BIG WHOOPS. Server does not work. My bad. Too many things going on. It DOES boot from the CD.

---

### Post by dcstar on 2007-03-29
> **reticulate said:**
> When installing 6.10 on an older IBM M-Pro install reports "Your CD-ROM could not be mounted. This probably means the CD-ROM is not in the drive........Try to mount the CR-ROM again?" This is after the CD boots and country is selected. Server installs fine.
BIG WHOOPS. Server does not work. My bad. Too many things going on. It DOES boot from the CD.

Check that the CD is set to Master device if it is the only device on the IDE channel, sometimes a Slave device without a Master will cause issues like this.

---

