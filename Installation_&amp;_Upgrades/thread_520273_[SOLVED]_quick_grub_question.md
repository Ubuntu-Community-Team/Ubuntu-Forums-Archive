---
title: "[SOLVED] quick grub question"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by sfgeorge on 2007-08-08
Howdy,

I've got hard drive with four partitions.  Typically, I would reference the 3rd partition (hda3) as (hd0,2).  However, I reorganized my partitions from this...
```
|           |           |           |           |
| /dev/hda1 | /dev/hda2 | /dev/hda3 | /dev/hda4 |
|           |           |           |           |
```
to this...
```
|           |           |           |
| /dev/hda1 | /dev/hda2 | /dev/hda4 | /dev/hda3 |
|           |           |           |           |
```

hda3 still has the same name, but in physical location it's the 4th partition.  Is it still (hd0,2) in grub-speak, or is it now (hd0,3)?

Thanks!

Stephen

---

### Post by aquavitae on 2007-08-08
Easiest way to find out - try it and see what happens.  How did you manage to change the physical location of a partition?

---

### Post by logos34 on 2007-08-08
> Is it still (hd0,2) in grub-speak

yes

---

### Post by sfgeorge on 2007-08-08
> **aquavitae said:**
> Easiest way to find out - try it and see what happens.  How did you manage to change the physical location of a partition?
Thanks, I did give it a go.  From your response and that of logos34, I'm confident that grub's partition numbering system for  (hd0,y) is based on the partition name, not physical location.

To satisfy your curiosity... I managed to do this with GParted.  :)

Stephen

---

### Post by sfgeorge on 2007-08-08
> **logos34 said:**
> yes

Thanks a bunch, just needed a confirm.

I actually was not able to install successfully last night, but I feel that the (hd0,y) that I entered was correct.  I'll mark this thread as solved, as you both did answer my question.

I'll post my current issue with installing on a different thread.

Thanks!

Stephen

---

