---
title: "hard disk partitioning"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by ged25 on 2010-03-08
I have a 150GB HD with XP installed. 100 GB is split into three logical drives (C,D,E) where my data is stored. 50GB is unallocated. I want to install Ubuntu here. Will using option two: Guided - use largest contigious free space be sufficient ?

---

### Post by sikander3786 on 2010-03-08
> **ged25 said:**
> I have a 150GB HD with XP installed. 100 GB is split into three logical drives (C,D,E) where my data is stored. 50GB is unallocated. I want to install Ubuntu here. Will using option two: Guided - use largest contigious free space be sufficient ?

Yes I have often installed Ubuntu the same way when I wanted to dual boot with Windows. Don't make a partition on the 50GB free space. Select Guided - use largest contigious free space and Ubuntu will automatically partition it and install /root, /swap in that space. And will automatically install GRUB to the MBR and will detect Windows XP for dual booting.

Regards.

Sikander.

---

### Post by newguy2010 on 2010-03-09
I also have this doubt. I don't have backup of my Window files so I've been scared to do this.

---

