---
title: "LibreCAD V1.01 to old in the Repos for Kubuntu 12.04 LTS"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by mue.de on 2014-06-15
Hello,

for some time i used QCAD 'til i had to setup a newer Laptop; now i installed LibreCAD from the official Repos for Kubuntu Precise (12.04 LTS).

Unfortunately it is an relative old Version (1.01). Could i safely use a GIT-Repo and install the newer Version 2.04, which has a new Interface to Qt4, as it is recommended at [http://librecad.org/cms/home/from-source/linux.html](http://librecad.org/cms/home/from-source/linux.html) ?
Or do i have to dist-upgrade to the next LTS-Version of Kubuntu 14.04 Trusty Thar ?

Any help will be appreciated, thanks in advance

mue.de

---

### Post by mörgæs on 2014-06-16
Have you tried Kubuntu 14.04 in a live boot? Here you get 2.0.2 without installing from git.

---

### Post by mue.de on 2014-06-17
Thanks for your help,

 i made a bootable Kubuntu 14.04 live usb-Stick and installed the newer Librecad 2.02 out of the box.

So far i can use it -but i have to reboot my laptop; could i instead install it in a virtualbox with that 14.04-System without much overhead (i've only an 80GB harddisk and an dualboot with win-7)

---

### Post by mörgæs on 2014-06-17
Why not erase 12.04 and do a fresh install of 14.04?

---

### Post by mue.de on 2014-06-17
Such an dist-upgrade means always for me a few weeks of 'after-work-party' ;-(

I've got -after long struggling- the following programs running and can't effort their malfunction in a new wonderful OS ;-)

 - Eclispe Kepler with AVR-Toolchain for C-Development 
- Apache Web-Server running a MoinMoin-Wiki
 - Digikam with thousands of kommented Fotos
 - Amarok with music colletion
 - Wine with FileSync, Silverjuke, Bid-o-matic ...
 - Kontact -where i'm still migrating old saved eMails, Kontacts -> Akondi-/neopmuk-Trouble is almost forgetten now, quite good runnig, now there is again an 'upgrade'

To have a newer version of Librecad is nice but it isn't worth risking a damage of the whole system

So, please be patient with me when I'm keeping a running system as long as responsable

---

### Post by mörgæs on 2014-06-17
Never dist-upgrade. That's why I mentioned a fresh install.

Another option is a dual boot with both 12.04 and 14.04. Then you can step by step migrate into 14.04 while keeping the old system working.

---

### Post by mue.de on 2014-06-17
Yes, that may be the right way, i can spent some amount of disk-space of the win-7 partition for the new Kubuntu Distro. I'll try it soon.

Thanks

---

