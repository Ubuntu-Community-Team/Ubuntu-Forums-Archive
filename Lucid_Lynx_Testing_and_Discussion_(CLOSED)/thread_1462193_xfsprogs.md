---
title: "xfsprogs"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jallain on 2010-04-25
I've been using xfs filesystem for years. xfsprogs has always been installed in Ubuntu up until the rc release. All of a sudden xfsprogs is missing. Does anyone know why?

---

### Post by howefield on 2010-04-25
It is still available..

[http://packages.ubuntu.com/lucid/xfsprogs](http://packages.ubuntu.com/lucid/xfsprogs)

---

### Post by 23meg on 2010-04-25
Are you sure it was *installed* by default? According to the ubuntu-meta changelog, it seems to be present on the live session only, since Ubuntu 6.10.

---

### Post by jallain on 2010-04-25
Yes, it's still availabe. However, I have to install the package before I install the rc. Prior to Lucid rc, xfxprogs was always installed as part of the live CD. I have to take the extra step of installing xfsprogs first. I'm just wondering why the change all of a sudden after all these years.

---

### Post by conradin on 2010-04-25
XFS is somewhat archaic, and better file systems now exist. XFS for example has only 2 superblocks per partition, ext3 has 8 or 16, there are more features in the journaling of the modern ext file systems than XFS. As for default hardware, Only Silicon Graphics International comes to mind for companies delivering products with XFS, and I'm almost certain they're not doing that any more. Ubuntu needs to stay relevant to modern hardware in order to be competitive. Still, if you look in synaptic package Manager, you can get xfsutils.

as for default XFS package inclusion, in 8.04 or later, Im not seeing it. There may be some overlap utilities like fsck that might have xfs support.

---

