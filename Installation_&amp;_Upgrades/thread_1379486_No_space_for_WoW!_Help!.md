---
title: "No space for WoW! Help!"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by mielclawson on 2010-01-12
I am wanting to install World of Warcraft and I have no space on my ubuntu partition. However I do have windows installed dual boot, and I have a separate partition from both that I use for large game files and what not. Is there a way I can install wow using this partition or one like it through Ubuntu?

---

### Post by phillw on 2010-01-12
> **mielclawson said:**
> I am wanting to install World of Warcraft and I have no space on my ubuntu partition. However I do have windows installed dual boot, and I have a separate partition from both that I use for large game files and what not. Is there a way I can install wow using this partition or one like it through Ubuntu?

Hi & welcome to the forum.

I'm surmising that your seperate partition, that you use for both is NTFS formatted (else Win couldn't see it)

You can use GParted to shrink that area by a few GB, then grow your Ubuntu area.

Whilst resizing partitions is pretty fool-proof, something like a power failure could really mess things up - So, do take a backup of important stuff !!

If you will post back here the results of 

```
sudo fdisk -l
``` that's a little L not a number 1
and also ```
df -hT
```We'll be better able to tell you what your options are.

Regards,

Phill.

---

