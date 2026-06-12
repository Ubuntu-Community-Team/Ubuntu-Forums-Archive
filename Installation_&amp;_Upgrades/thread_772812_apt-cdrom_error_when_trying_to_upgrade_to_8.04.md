---
title: "apt-cdrom error when trying to upgrade to 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by nobloodshed on 2008-04-28
im running gutsy gibbon, and i am trying to upgrade to the newest ubuntu release, 8.04, and after about three minutes in the installer, it gives me this error
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


i have no idea what to do, and can someone please help me?
also sudo apt-get upgrade and sudo apt-get update dont work.

---

### Post by nobloodshed on 2008-04-30
could someone please help me? i really want to upgrade

---

### Post by nobloodshed on 2008-04-30
can someone please help me?
or am i in the wrong forum?

---

### Post by nobloodshed on 2008-05-02
so is there anyone here who is going to help me?
im running 7.10 and yet it gives me an error about requiring the cd's from 7.04.  ive seen many other threads getting help, and yet im not?
i really want to upgrade to 8.04.  could someone please help?

---

### Post by analyzer123 on 2008-05-02
What you could try is... modify your /etc/apt/sources.lst file and remove the entry which lists the feisty cdrom. So that the update manager is forced to download from the internet. Try if it works.

you can google for more info about sources.lst

---

### Post by howefield on 2012-12-28
Desist from resurrecting old threads.

Closed.

---

