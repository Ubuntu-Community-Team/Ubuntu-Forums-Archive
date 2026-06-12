---
title: "copy error while installing Ubuntu netbook along with XP leaving a partitioned drive"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by Milkman08 on 2010-12-30
I want to undo all edits to HDD and start installing Ubuntu NetBook with the .iso file freshly burned on a new disk ... but I don't know if undoing the partitioning using gparted cd I have would cause my XP installation to be removed or not ... is it safe to do it? if not, is there a safe method?

---

### Post by mikewhatever on 2010-12-30
Not sure what you mean by undoing. Last time I checked, Gparted didn't have an 'Undo' button. If you simply want to resize the partitions back to what they were and delete the partitions you created, that should be safe. As log as you don't delete or format the Windows partition, it won't be removed.
The question is, what do you want undone.

---

### Post by Milkman08 on 2010-12-30
[QUOTE=mikewhatever]If you simply want to resize the partitions back to what they were and delete the partitions you created, that should be safe. As log as you don't delete or format the Windows partition, it won't be removed.[/QUOTE]
That's exactly what i meant by undoing :) OK, so, you're saying nothing will happen to my XP install if I just remove the swap drive and ext4 formatted drive and resise the XP partition using gparted ... right?

---

### Post by WthIteh on 2010-12-30
> **Milkman08 said:**
> That's exactly what i meant by undoing :) OK, so, you're saying nothing will happen to my XP install if I just remove the swap drive and ext4 formatted drive and resise the XP partition using gparted ... right?
Removing ext4 and swap partitions is completely safe.
But resizing your XP partition is not so (it is dangerous always).
If you want to do a fresh Ubuntu install after undoing your previous operations, you do not need that undoing work at all. Just start installation process and when you reach the partition selecting page, select to do it **manually** and there select partitions which you want to be used as your root partition. You could tell installer there to format that partition too.
DO NOT RESIZE XP PARTITION IF YOU ARE NOT FORCED TO DO IT.

---

### Post by mikewhatever on 2010-12-30
> **Milkman08 said:**
> That's exactly what i meant by undoing :) OK, so, you're saying nothing will happen to my XP install if I just remove the swap drive and ext4 formatted drive and resise the XP partition using gparted ... right?

That should be safe, not quite sure what WthIteh means.
What's the copy error you mentioned in the title?

---

