---
title: "HD partitioning issues….. Please help…."
date: 2006-08-14
forum: Installation &amp; Upgrades
---

### Post by Firecub on 2006-08-14
Hi Guys,
I am stuck in a problem… I am trying to do an alternate install of Ubuntu in the “Text mode”. This is the second time of me doing it. The last time I did I was able to partition the hard drive into a 10 partition for Ubuntu, leaving the rest of the HD for windows. This time around It is forcing me to make a partition of at least 18 gigs. I don’t get it?
All help will be appreciated.

---

### Post by john_spiral on 2006-08-14
Looks like the Ubuntu installer is having problems seeing your Windows partition. Try booting off the Ubuntu CD and running:

sudo fdisk -l 

from a terminal.

It wil display your partitions. Are you installing from a CD?

---

