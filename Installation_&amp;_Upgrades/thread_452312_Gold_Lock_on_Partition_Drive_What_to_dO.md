---
title: "Gold Lock on Partition Drive? What to dO?"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by dangqt85 on 2007-05-23
Hi I m a new Linux user and I am using feisty and trying to partition my drive with gparted and  I cant do it because theres a gold pad lock on it, why is that? and what do i do to partition the drive so I can dual boot window xp?

Thank you.

---

### Post by apunc1 on 2007-05-23
is the drive you're trying to partition mounted (i.e. in use)?
boot up with the live cd so you can use gparted on unmounted partitons.
from psycocats:

> You must use a live CD for this process for two reasons:

   1. In order to resize your existing / partition, it needs to be unmounted. The only way to unmount it is for it not to be in use, which means you can't boot to your regular Ubuntu installation while resizing it... which means you need a live CD
   2. If you screw up your installation by accident, you can use the live CD to restore your old settings and, in the worst situation, at least recover your important files

---

### Post by apunc1 on 2007-05-23
> **dangqt85 said:**
> and what do i do to partition the drive so I can dual boot window xp?

Thank you.

is feisty the only operating system on the hard drive right now?

---

### Post by hexadecimal on 2007-08-13
ok, im still geting the lock from the cd, not just on linux but on windows partitions also have the gold locks.

screenshot available at request.

---

### Post by sol0 on 2007-08-27
just for the record; the gold lock tells you that you can not partition the current drive because it is 'mounted'.

---

### Post by wislon on 2007-08-27
I've come across a similar problem once the drive's been partitioned and formatted. I found I had to use 'chown' on the empty drive before I could write to it. my guess is tho, that if you've got to the point where you want to partition it, and it's locked, that's probably because it's mounted.

Try (from a terminal):
cat /proc/partitions

which should show you which partitions are on what devices (if any). 

Once you have figured out which device it is that you need to repartition, just do a 

sudo umount /dev/sdax (where x is the device you want to partition, e.g. sda1 would be the first partition).

HTH :)

---

