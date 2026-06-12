---
title: "Highpoint Rocket Raid 133 RAID-Controller (Chipset HPT372)not operational"
date: 2005-06-30
forum: Installation &amp; Upgrades
---

### Post by mufftin on 2005-06-30
Hi there,

I tried to install Ubuntu 5.04. When I am asked to setup my partition
the installsystem prints an error that there aren't any harddisks to setup.

I have a Highpoint Rocket Raid 133 controller. I've set up a RAID0-array
with two 160GB harddisks. Can I use another "driver" or is this
controller that bad that it isn't supportet under Linux/Debian?

Sincerely, Martin

---

### Post by mingus on 2005-06-30
A quick google turned up . . .

[http://www.highpoint-tech.com/USA/bios_rr133.htm](http://www.highpoint-tech.com/USA/bios_rr133.htm)

but also this thread . . .

[http://nixdoc.net/files/forum/about14759.html](http://nixdoc.net/files/forum/about14759.html)

Look at the other google hits.  I've seen posts re fakeraid controllers being supported in the 2.10 kernel, but nothing certain.

Probably can use a straight IDE setup, it's the RAID that is the issue.

---

### Post by mufftin on 2005-06-30
Hi Mingus,

thank you very much. You _really_ helped me.
Kicking RAID :-|

Sincerely, Mufftin

---

### Post by mingus on 2005-06-30
You're welcome.  Glad to have been of some help . . .

---

