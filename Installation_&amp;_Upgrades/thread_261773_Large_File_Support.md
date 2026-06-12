---
title: "Large File Support?"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2006-09-20
Does Ubuntu have large file support compiled in?

I just backed up my Ubuntu partition using partimage (I cloned 5 systems with Ghost as I was familiar with it already) and noticed that the ext3fs summary partimage printed at the end showed "Large File Support NO"

Its possible Ghost has cleared the flag, if so anyone know how I restore it, or otherwise enable large file support in Ubuntu?

In the mean time I can boot the original system I cloned and back up its partition to see if Ghost has cleared the ext3 large file support flag or not.

--wally.

---

### Post by wkulecz on 2006-09-20
Just booted the original system I cloned from and partimage says "Large File Support NO".  Ghost is not supposed to touch the data it backs up, but I can't be 100% sure it didn't clear this flag when it started.

So the question appears to be how do I enable large file support in Ubuntu?

Partimage seems lame compared to ghost, can't restore to a partition smaller than the one backed up despite the smaller partition being 10X the size of the actual data on the partition that was backed up.

--wally.

---

