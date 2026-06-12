---
title: "Hard Drive Partition Problem"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by keithk50 on 2007-03-11
Hi,    Okay, used the GParted with the live CD to resize the windows partition of my laptop:

Results are:

/devhda1       Fat32             4.001     ...         ...                                                       Hidden
/dev/hda2      ntfs               13.32                 10.57                    2.75GB  Boot
unallocted     unallocted    3.42                   ...                          ....
/dev/hda3      Ext3                6.87                   3.58                     3.29                     3.29
/devhda4       Extended   337.31M
     /devhda5  Linux swap337.27MB

I really want to give my Ubuntu ((hda3) more space.   I am now at a complete loss.   Looked for help via the forums and have really tried to do this without asking for anymore help.    The result of my endeaver is a unollated space of 3.42GB (what I asked for).   My question is how do I allocate this spare space to Ubunto (hda3).   
Only been with Ubuntu for 3 weeks so please be gentle.     Thanks.

---

### Post by tallman9 on 2007-03-11
so you used the GParted liveCD?
create an ext3 partition of that unallocated space and merge it with your ubuntu partition.

---

### Post by keithk50 on 2007-03-11
Thanks for the interest.   I do not know what you mean.   Could you please be a little more specific.
Thanks.           Keith

---

### Post by tallman9 on 2007-03-12
what specificaly you didn't understand? =)
check this link for GParted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by zvacet on 2007-03-12
Format unallocted partition to ext3 format and add it to existing ext3 partition.

---

