---
title: "updating broke my desktop"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by raiwo on 2008-11-10
i just did update by update manager & started having problems: my programs (for example system monitor) didn't star anymore so i did a reboot. So when my machine boot after when desktop should come i got following error:

```
loading please wait...
19.10 regords in
19.10 regords in

kinit: name_to_dev_t(/dev/disk/by-uuid/2ca24eda-08ac-4b71-a7dd-7b06d4fda63c) =dev(8,6)

kinit: trying to resume from(/dev/disk/by-uuid/2ca24eda-08ac-4b71-a7dd-7b06d4fda63c

kinit: no resume image, doing normal boot...
ubuntu 8.10 mli tty1
 
```
after that i logged in in text mode & strated to start gnome-panel & got error

```
error while loading shared libraries: libpango-1.0.so.0: cannot open sharedobject file:no such file or directory
```

i also tried to udate  my machine apt-get update but didn't get any updates to fix this.

So how to fix this (tried older kernel, didn't help) ubuntu 8.10

---

### Post by raiwo on 2008-11-10
so, tried to strat gnome by gdm i got that i am missing file libpangoft2-1.0.so.0 tried to apt-get install libpangoft2-1.0.so.0 but couldn't find package for some reason? I also did apt-get update & apt-get upgrade but no help

what to do?

---

