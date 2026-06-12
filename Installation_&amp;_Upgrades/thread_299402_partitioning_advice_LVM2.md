---
title: "partitioning advice LVM2"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by theorem_hunter on 2006-11-14
i have a 120 gig ide hard drive that has only ubuntu on it. there is a 119gig / partition & a 1gig swop partition. 

i want to format & re install but i need sum advice. i want to also use the drive in a external hdd case to take to friends to share things on the drive. 

more importantly i want to use LVM2. so i want a / partition for all system stuff, a /home partition for all my stuff & then a /sharedata partition that i can use to share things.

i would like all the drives to be ext, even the sharedata. i think windows pc's can read it with a ext2ifs driver (does anybody know if i will still work when i put the drive in a usb2 external hdd case?)

what sizes should i use for the partitions or if anybody has done something like this before then please let me know what your set up was. 

(i like installing random things from the repos  & were ever else i can find things to install, so if / needs to initially be big its ok)

or is this something i dont need to worry about because the lvm will dynamically resize partition as they need to be?

thanks :confused:

---

### Post by cotcot on 2006-11-14
Windows with fs-driver can read ext3 from external usb.
Lvm2 does not dynamcially resize the partitions. It is however easy to change the size manually. If you reinstall ubuntu take the alternate install cd (the normal cd does not support lvm2).
Partition sizes are not different as for an install without lvm.
(for instance: 20 G root, 2 G swap, rest home). I would not take the external usb disk in the lvm.

---

### Post by theorem_hunter on 2006-11-14
thanks,

well i hav a alternate install cd, but i did not see a option to install lvm2 when i was partitioning so i just did with out lvm. used the same partition configuration as i had before, but would like to ask, if i want to make a new partition is it do-able? right now i have a 119gig / partition but if later on i think i will need a /something partition, will it be easy to do with out messing up the system?

thanks

---

### Post by synss on 2007-03-07
> **cotcot said:**
> Partition sizes are not different as for an install without lvm. (for instance: 20 G root, 2 G swap, rest home). I would not take the external usb disk in the lvm.

Agreed for the ext. USB HD.

But not for the partition scheme. If it is the same, then what is the point of using LVM? So I would recommend as small as possible for root (4Gb here) and pretty big for /home but **not** all the rest!!! leave some place to grow or shrink your partitions, that is the whole big point for using LVM!

I do not know whether hibernation will work if swap is on LVM (that is a question).

---

