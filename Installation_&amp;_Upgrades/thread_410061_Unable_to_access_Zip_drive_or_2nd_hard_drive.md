---
title: "Unable to access Zip drive or 2nd hard drive"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by alfreddo on 2007-04-15
Having installed Ubuntu 6.01 on a PC that previously ran Windows 98, I find I cannot access either the second hard drive (used for backups and archives), or the Zip drive. Both are shown to exist.

I put a disk in the zip drive and tried to open it. Got this message:

Could not mount zip drive
Unable to mount the selected volume
error: device  /dev/hdd4 does not exist
error: could not execute pmount

When I tried to access the second hard drive (partitioned by Windows under FAT 32), I got this message:

error: device  /dev/hdb/ is not removable
error: could not execute pmount

Any suggestions will be gratefully received

---

### Post by confused57 on 2007-04-15
You need to create mountpoints and mount your drives:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

also, see the 2nd link in my signature

---

### Post by alfreddo on 2007-04-15
Thanks for that, confused57.  I'll work through the page you directed me to.

You're confused? You should see me...

(By the way, the second link in your signature leads to a 'server error' message.)

---

