---
title: "LVM related question"
date: 2007-08-01
forum: Installation &amp; Upgrades
---

### Post by jml75 on 2007-08-01
Hi

I'd like to reinstall my system but I have a question regarding an LVM partition I have.

I have 4 partitions, one ext3 for "/boot", one ext3 for "/", one swap and one LVM xfs partition on a RAID array for data.

Can I format my system partitions, reinstall Linux and then be able to remount my LVM partition in the new install without loosing data?

Thanx!

---

### Post by talby on 2007-08-01
Yes, once you have the RAID attached to the system run:

"pvscan" to scan for type 8e physical volumes and let lvm know there are there.
"vgscan" to recognize volume groups in said physical volumes.
"lvscan" to search for logical volumes in said volume groups.
and finally "vgchange -a -y {*volumegroup-names-here*}" this will allow access to the logical volumes.

Then you should be able to mount it no problem.

---

### Post by jml75 on 2007-08-01
Thanx a million Tlaby.

It worked pefectly but I found out that you made a small mistake in the last command you told me to use.

Instead of "vgchange -a -y {*volumegroup-names-here*}".

It needs to be "vgchange -a **y** {*volumegroup-names-here*}"

No "-" for the letter "y".

Thanx again!

---

