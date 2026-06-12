---
title: "[SOLVED] is archive mounter working for you?"
date: 2008-09-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by excogitation on 2008-09-18
When I mount an iso with archive mounter e.g. intrepid-desktop-i386.iso - it shows up in nautilus places pane, but as soon as I try to open (click) it nautilus closes.

It's still mounted when I open nautilus again and nautilus closes again if I click on it.

Where does it mount to? (I couldn't find a mountpoint in /media nor in /mnt)

Also - if it worked - could I modify archive mounter to mount iso's with multiple partitions which I get e.g. ```
pv /dev/sdx > /image_of_sd_card_with_multiple_partitions.iso
```

---

### Post by plun on 2008-09-18
Nope, it crashes and I filed a bug about it.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343)

Gnome upstream
[http://bugzilla.gnome.org/show_bug.cgi?id=547468](http://bugzilla.gnome.org/show_bug.cgi?id=547468)


No activity for some time....

---

### Post by excogitation on 2008-09-18
Thanks ... wait and see?

---

### Post by mc4100 on 2008-09-18
I just tried it with an .iso I made recently of a DVD, it worked fine for me.
Right Click -> Open with "Archive Mounter"
(... it shows up as a drive on the Desktop.)
And displays it's contents in Nautilus (which doesn't crash).

---

### Post by dracule on 2008-10-28
file names are messed on w/ mine

and it is super slow.

---

### Post by excogitation on 2008-10-28
The nautilus issue has been resolved through an update.

---

### Post by FuturePilot on 2008-10-28
It's still crashing for me.

---

