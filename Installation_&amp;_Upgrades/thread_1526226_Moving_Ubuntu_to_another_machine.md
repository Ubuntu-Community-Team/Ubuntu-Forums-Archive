---
title: "Moving Ubuntu to another machine?"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by h4x0rmx on 2010-07-07
I'm getting a new HD on my laptop so I'm wondering if I can move the installation of Ubuntu to the new HD without much hassle since the hardware is the same, but the size of the partitions is bigger?
I have a lot of configurations and stuff that I don't want to loose, nor do I want to install everything again.
Any suggestions?

P.S. I have an external HD where I can make a backup if necessary, so that wouldn't be a problem.

---

### Post by amauk on 2010-07-07
easiest is putting the new disk in the machine with the old disk, booting to a liveCD, and dd'ing the data from one drive to the other
after this, you can remove the old disk

say the old disk is /dev/sda, and the new disk is /dev/sdb, then
```
dd if=/dev/sda of=/dev/sdb
```

This will make an exact copy of sda to sdb
so if the new disk is bigger, you'll have an unpartitioned bit at the end of the new disk

Still with the liceCD, you can expand the partitions how you want to make use of the new space

*edit*
just re-read your post and noted it's a laptop
If you can't have 2 disks in at the same time,
you may need to do this in stages, using your external disk

liveCD
dd from old to external disk
switch drives
dd from external disk to new

---

### Post by h4x0rmx on 2010-07-07
@amauk  I'm getting rid of my current HD before I get the new one.  Could I copy the partitions into my external HD using dd? (and then copy that into the new HD?)
I would have to partition my external HD, right? Will it need to have the same file format?

---

### Post by amauk on 2010-07-07
> **h4x0rmx said:**
> @amauk  I'm getting rid of my current HD before I get the new one.  Could I copy the partitions into my external HD using dd? (and then copy that into the new HD?)
see my edit
> **h4x0rmx said:**
> Will it need to have the same file format?No, you don't have to do anything
the dd will copy everything from your old disk
All partitions, all data, even the boot loader
it'll be an exact copy

---

### Post by h4x0rmx on 2010-07-07
> **amauk said:**
> see my edit
No, you don't have to do anything
the dd will copy everything from your old disk
All partitions, all data, even the boot loader
it'll be an exact copy

I just realized that I'd be copying the data whole drive, right?
Is there a way to copy just the partitions?  I have windows (bc of work) installed on the same HD, but I'm downgrading it.  I don't really care about the data in the non-linux partitions. (and my external HD is not empty)
What would you suggest?

---

### Post by amauk on 2010-07-07
if you want something more configurable,
maybe look into Clonezilla

It's a LiveCD designed for easily cloning disks and/or partitions
and it'll be more flexible than straight dd

---

### Post by h4x0rmx on 2010-07-07
> **amauk said:**
> if you want something more configurable,
maybe look into Clonezilla

It's a LiveCD designed for easily cloning disks and/or partitions
and it'll be more flexible than straight dd


I'll look it up!
Thanks!!!

---

