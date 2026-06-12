---
title: "Swap Partition for Two Operating Systems"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by luimichael on 2008-02-06
Hello! 
If want to I have 2 versions of linux in the same hard disk, how many swap partitions do I need to prepare?
And is it possible to share a swap partition for 2 operating systems?
Hope someone can help me.

---

### Post by forestpixie on 2008-02-06
you can just have one swap partition - when you install either they'll pick it up or you can point the way

---

### Post by az on 2008-02-06
You can share a swap between two or more Linux Oses, but you can't use the suspend-to-disk (hibernate) function.

When you hibernate, the contents of your ram get written to the swap.

---

### Post by dicecca112 on 2008-02-06
if one was to partition a drive from the Live CD, would it matter where you put the swap, ie Should you go ext3 part for OS1, ext3 part for OS2 then swap or what?

---

### Post by forestpixie on 2008-02-06
> **az said:**
> You can share a swap between two or more Linux Oses, but you can't use the suspend-to-disk (hibernate) function.

When you hibernate, the contents of your ram get written to the swap.

Didn't know that - do now :) - never having actually used hibernate

And where's Kirk - has he boldly gone...

---

