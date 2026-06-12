---
title: "GRUB update vs. install devices (does not recognise /boot at RAID1 device?)"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by SaturnusDJ on 2010-05-06
Things to know:
/boot is on a RAID1 array (/dev/sda1 and /dev/sdb1).

[IMG]http://i41.tinypic.com/bf2cr4.png[/IMG]

[IMG]http://i41.tinypic.com/10dhydi.png[/IMG]

Above shows the standard selected drives.

I changed it to /dev/sda1 and /dev/sdb1 and got:

[IMG]http://i44.tinypic.com/2ik8xax.png[/IMG]

[IMG]http://i41.tinypic.com/x55lok.png[/IMG]

After some thinking I find out that none of the options above could be correct. /dev/md0 is the only correct device to install, right?
Should I continue? (No brings me back to the first screenshot.)

---

