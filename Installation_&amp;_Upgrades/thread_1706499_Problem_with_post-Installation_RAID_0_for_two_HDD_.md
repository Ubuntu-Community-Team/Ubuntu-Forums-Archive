---
title: "Problem with post-Installation RAID 0 for two HDD (SATA)"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Farrukhjon on 2011-03-13
Hi guys!, A have problem with post-installation RAID0 for my two SATA HDD. In partition step i choose configuration RAID0, success create RAID MD0:
MD0 / 312 gB
/dev/sda1---swap
/dev/sda5---/ (boot)
/dev/sdb1---swap
/dev/sdb5---/ (boot)
When i logged as root and try:
grub-install --no-floppy /dev/sda
grub-install --no-floppy /dev/sdb 
for degraded booting but the console print I/O error f0 --missing...and more info...
Help me , where i have do wrong.

---

### Post by Hedgehog1 on 2011-03-14
Raid 0, or striping look like this across two drives:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/RAID_0.svg/150px-RAID_0.svg.png[/IMG]

Once the set up, the two 'striped' drives need to present themselves as a single 'larger' drive.

So a RAID0 of two 160 gig drives would appear as a single 320 gig drive (/dev/sdb).

Your setup:

> MD0 / 312 gB
/dev/sda1---swap
/dev/sda5---/ (boot)
/dev/sdb1---swap
/dev/sdb5---/ (boot)

should really look like this:

/dev/sda <- tiny boot & OS drive (Possibly SSD?), 20-40 gigs
/dev/sdb <- Stripped set of RAID0 drives, which holds '/home/ & 'SWAP'

What RAID card are you using to make the RAID0?  Do you have a separate boot drive/SSD?

***The Hedge***

:KS

---

### Post by Farrukhjon on 2011-03-14
I'm using mdadm, ie software RAID and i guide using this tutorial [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Hedgehog1 on 2011-03-14
Ahh yes..  Software raid...  

The guide indicates that:

> Warning: the /boot filesystem cannot use any softRAID level other than 1 with the stock Ubuntu bootloader

If you are booting from the SOFTWARE raid, you must use RAID 1.

Are you booting from the software RAID?

***The Hedge***

:KS

---

### Post by Farrukhjon on 2011-03-14
Yes i use sofware RAID, and i need to up degraded boot in my case :
two hdd (sda and sdb) each hdd have size of 160 gb and md0 uped each /dev/sdX have boot flag. But i whant boot my system if my first hdd would be halt down. Recomend me how do it.

---

### Post by Hedgehog1 on 2011-03-14
The least-painful way is this:

3 drives; the two SATA drives you already have, and a small SATA drive

/dev/sda <-- small SATA drive, Mounts '/' & (and therefore '/boot', too)

/dev/sdb & /dev/sdc (they make up your RAID, and mount '/home' & 'SWAP'

This gives you a predicable boot drive (one small SATA) and the RAID for speed.

***The Hedge***

:KS

**p.s. According to the Guide, they suggest 2 RAIDs, a little RAID 1 to boot, and then your RAID 0,5 or 6 for bulk data storage.**

---

### Post by Hedgehog1 on 2011-03-14
By the way, you likely already know this, but just in case:

RAID 0 is fast, but very risky.  If any one drive fails, all data is lost.

RAID 1:

[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/b/b7/RAID_1.svg/150px-RAID_1.svg.png[/IMG]

Will give your even better Reading performance, but slower Write performance.  However, it will survive a hard drive failure.

It does mean you need two 320 gig drives to get a 320 RAID 1.  But it is really worth it.

Also, software RAID is fine for learning.  Hot-swappable hardware RAID is the best choice for critical servers.

***The Hedge***

:KS

---

### Post by Farrukhjon on 2011-03-14
Can i remove my MD0 RAID device without loss my data and recreate new RAID1 for mirrorize and degraded boot ? for example:

mdadm --create /dev/md0 --chunk=64 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdb1

---

### Post by Hedgehog1 on 2011-03-14
> **Farrukhjon said:**
> Can i remove my MD0 RAID device without loss my data and recreate new RAID1 for mirrorize and degraded boot ? for example:

mdadm --create /dev/md0 --chunk=64 --level=raid1 --raid-devices=2 /dev/sda1 /dev/sdb1

Yes - this is a very good solution using the hardware you have on hand.  It will give you a 160 gig RAID, and it will boot and still be a RAID.

***The Hedge***

:KS

[B]p.s. The reason the software raid needs RAID1 is that right as it boots, it really uses /dev/sda by itself to boot, so that disk needs to be 'complete' and not striped.
[/B]

---

### Post by Farrukhjon on 2011-03-14
Thanks, i would try it, and thank you very much, i glad that discuss with you. Good luck!

---

### Post by Hedgehog1 on 2011-03-14
We are here if you need us again!  Drop in any time...

Best of luck!

***The Hedge***

:KS

---

