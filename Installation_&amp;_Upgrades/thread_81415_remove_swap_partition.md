---
title: "remove swap partition?"
date: 2005-10-24
forum: Installation &amp; Upgrades
---

### Post by Josef K. on 2005-10-24
Since I got 1Gb RAM I wonder what happen if I completely remove swap partition: the system will go slower or faster?

---

### Post by matthew on 2005-10-24
[quote=Josef K.]Since I got 1Gb RAM I wonder what happen if I completely remove swap partition: the system will go slower or faster?[/quote]
Most likely neither. The swap partition is probably not being used now unless you have a very large number of memory hungry programs open at the same time so removing it won't change how the system is operating. If you have the extra disk space to spare, leave the swap there for those extremely rare times you may want to open Gimp, run a CAD program, play a 3-D game and crunch numbers on a large spreadsheet at the same time.

---

### Post by flower on 2005-10-25
my advice is - get rid of the swap partition,
and mount the swap point in a subfolder of primary partition ...

---

### Post by withoutclass on 2005-10-25
[QUOTE=flower]my advice is - get rid of the swap partition,
and mount the swap point in a subfolder of primary partition ...[/QUOTE]

do this if, when your system does need to use swap, you like your system to be even slower at accessing the swap drive

---

