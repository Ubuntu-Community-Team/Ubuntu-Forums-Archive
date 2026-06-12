---
title: "Installer Only Detects 1 Hard-Drive"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by jarrhed on 2011-05-21
My hard-drives are setup as follows:
[LIST]
[*]2x32gb SATA
[*]1x1.5TB Sata
[*]1x160gb SATA
[/LIST]
It's in AHCI Mode on the SB700 Chipset

I never had this problem with any other version of Ubuntu

When in the LiveCD environment (as in Gnome and all), It detects my other hard-drives and is able to mount them.

[IMG]http://i.imgur.com/u1I7G.png[/IMG]

**[SIZE="3"]Why won't it detect my other hard-drives in the installer? How can I get it to detect my other hard-drives in the installer?[/SIZE]** (This is a problem because I want to install Ubuntu on my 160gb hard-drive

Please note that all of my hard-drives are in working condition.

---

### Post by oldfred on 2011-05-21
Post this:
```

sudo fdisk -lu
```

---

