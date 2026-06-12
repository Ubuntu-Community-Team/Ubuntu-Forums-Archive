---
title: "Gutsy beta install problems hd becomes sd, error 15 on restart"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2007-10-11
Two attempts to install gutsy beta on the test mule (see tag line below). 

 First (minor):   my IDE drives are denoted as sd0, & 1;  not hd0, & 1.

Second (not minor):   after loading desktop system from disk and restarting, I get "ERROR 15 File not found"  "hit any key to continue"  I hit return and get to the list of systems and recovery versions on this and a second disk (that has a feisty myth install).  All options (except memtest) return to "ERROR 15 File not found"

The disk was checked on the box's drive 40X, and the second attempt was made with a 4X drive that would install when other drives wouldn't.

Any ideas?

---

### Post by zvacet on 2007-10-12
[http://users.bigpond.net.au/hermanzone/p15.htm#15]("http://users.bigpond.net.au/hermanzone/p15.htm#15")

---

### Post by Panhead Bill on 2007-10-15
The 7.10 desktop beta was installed onto the IDE2 master drive, 7.04 server/mythtv is on IDE1 master.  Grub has them transposed; 7.10 desktop beta is listed as being on hd0,0 - while the 7.04 myth is listed as hd1,0.  If I select and then edit the drive number (i.e. change hd0,0 to hd1,0) then 7,10 will fire up.

---

