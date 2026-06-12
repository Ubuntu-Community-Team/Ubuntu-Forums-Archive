---
title: "Install of Maverick on RAID5 works but Raid broken"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by GrampsPJR on 2010-10-24
I have three 1TB Hitachi hard disks in RAID5 that worked well with Windows XP, Jaunty and Karmic.    I did an install of Maverick using the automatic "load along side existing OSs" and it went smoothly and I have installed the ATI Centre and HP printer software and every thing works.    However when I do a System, Administration,Disk Utility check I find that the first hard disk shows all the original partitions, unchanged, the second disk shows as unallocated space and the third hard disk now shows as 991GB ext4 plus 9.4GB of extended swap.
The SATA Host Adapter in the LH column ens with [RAID5 mode} still.
I built the computer earlier this year aiming to use RAID 5 to avoid all the hassle of losing data when hard disks go u/s and I haven't found a text to guide me but it appears to me that I now have three independent disks rather than one RAID 5 installation.    Help, where do I go from here?

---

### Post by psusi on 2010-10-24
There's nothing wrong; just ignore the physical disks.

---

### Post by GrampsPJR on 2010-10-25
Thanks for the advice

---

