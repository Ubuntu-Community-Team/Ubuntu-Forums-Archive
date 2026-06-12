---
title: "ubuntu server on dell poweredge 2450"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by liathus on 2008-04-20
Hello, I am trying to install Ubuntu Server 8 RC on a dell poweredge 2450.  Everything went fine during the install, ubuntu detected and let me install on my hardware raid volume.  However, after the installation completed, and upon reboot, i am faced with some nasty errors.  Im not sure why the server install cd could detect and mount the volume properly but it doesnt work after reboot.  I have listed errors below.

Please note, that i was intending to move our production servers (also using dell raid) to ubuntu from gentoo, but that isnt gonna happen if i cant get this fixed, plese help so I dont have to waste years of my life waiting for source to compile anymore  :)


e.g.

aacraid: Host adapter abort requesr. SCSI hang?

and after a bunch of those i get

check root = bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/(inser my uuid here) does not exist. Dropping to a shell!

---

### Post by liathus on 2008-04-20
Dang I was hoping someone would have had some advice by the time I got home:)

---

### Post by Spartan.II.117 on 2008-04-20
you probably want to post this in the server section, a they would be more help with raid.

---

