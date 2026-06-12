---
title: "comand line install can't find package"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Mukumbu on 2008-12-01
I did the command line install on an old amdk6-2 desktop with 384mb ram and 13. gb hd from the xubuntu 8.10 alternate cd.  It seemed to install with no problems but the network connection did not configure.  There is a Belkin USB wireless adapter but not a way to use a wired connect.

When i try to sudo apt-get install for the minimal desktop and package manager I get the "couldn't find package xorg". 

Is there a way get the files off of the cd?

Thanks.

---

### Post by oldos2er on 2008-12-01
Go to System, Administration, Software Sources to enable the CD-ROM/DVD.

---

### Post by snowpine on 2008-12-01
Or, since command line installs don't have a System menu :):

```

sudo apt-get cdrom
sudo apt-get update
sudo apt-get install ...

```

---

### Post by oldos2er on 2008-12-01
Oops, my bad.

---

### Post by Mukumbu on 2008-12-02
I tried the apt-get cdrom but get the "E: Invalid operation cdrom"

Any other ideas?

---

