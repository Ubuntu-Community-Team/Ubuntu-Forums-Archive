---
title: "Hide GPT partition with GRUB2"
date: 2016-11-13
forum: Installation &amp; Upgrades
---

### Post by andreas53 on 2016-11-13
With MBR, a partition can be hidden by simply using parttool. However, GRUB2 has no parttool for GPT.
Is there any alternative to hide GPT partitions in GRUB2?

---

### Post by oldfred on 2016-11-13
Do not know details, but it is there.

in 
man gdisk

>    a      Set attributes. GPT provides a 64-bit attributes field that  can

   be  used to set features for each partition. gdisk supports four
  attributes: system partition,  read-only,  hidden,  and  do  not
  automount.  You  can  set  other  attributes,  but their numbers
  aren't translated into anything useful. In practice,  most  OSes
  seem to ignore these attributes. 



---

### Post by andreas53 on 2016-11-27
But gdisk is a Linux tool, right?
I was looking for a solution in GRUB2.

---

### Post by oldfred on 2016-11-27
In grub the hidden command is only for MBR(msdos) and for multiple FAT partitions to hide one or the other.

What is it that you want to do?

---

### Post by andreas53 on 2016-12-04
Since GPT has also a hidden attribute, I am looking for an option to set this attribute.

---

