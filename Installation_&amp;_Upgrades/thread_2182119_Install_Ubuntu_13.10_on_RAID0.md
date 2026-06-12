---
title: "Install Ubuntu 13.10 on RAID0"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by tiberiup on 2013-10-20
Hi, i made a fake/bios RAID0 from 2x 640 GB, on install it detect a 1,3 TB device,  if i select auto install or i make manual partition (ext4, swap, boot)  i get this error after i press install :
[http://postimg.org/image/j07db1ucx/](http://postimg.org/image/j07db1ucx/)

Any ideas ?

LE : this how partition look with Gparted on Live USB, i created a partition ext4 and copied files on that, all works ok.
[[img]http://s15.postimg.org/efu8j6ouf/Screenshot_from_2013_10_20_15_12_26.jpg[/img]](http://postimg.org/image/efu8j6ouf/)
[[img]http://s2.postimg.org/klhzvtdt1/Screenshot_from_2013_10_20_15_25_14.jpg[/img]](http://postimg.org/image/klhzvtdt1/)

LELE : i solved this by manual create all partition from live usb with Gparted (/boot, /swap, /)

---

### Post by forums-etarq on 2013-12-04
Thank you for posting this! I ran into this same issue.  I was able to choose the "Erase Entire Disk" and also use the "Use LVM" option and the install proceeded without any of the ??? ??? error boxes at the Time Zone screen!

---

### Post by christopher5 on 2014-02-20
LVM, why does this fix it? Thanks for the help!

---

