---
title: "adding another os"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by Lowfront on 2007-01-06
I Can't decide to try 64bit ubuntu or opensuse

anyways I have a 10gig fat 32 partition I set up for another os.

How should I partition that 10 gigs?

Can I use 1 linux swap for both os's?



So do I take that 10gigs and make a 5gig ext3 root and 5 gig ext 3 home?

---

### Post by Spano on 2007-01-06
> Can I use 1 linux swap for both os's?
Yes
> So do I take that 10gigs and make a 5gig ext3 root and 5 gig ext 3 home?
That's how I would do it.

---

### Post by jpkotta on 2007-01-06
It really depends on how your other partitions are set up.  You can only have 4 or fewer primary partitions, or 3 or fewer primary plus one extended partition with up to 15 (16?) logical partitions.  A utility like fdisk, cfdisk, or gparted will tell you and can edit partitions.

You can use the same swap partition for all OSes.

If it were me, I'd set up all OSes to use a common /boot as well.

---

