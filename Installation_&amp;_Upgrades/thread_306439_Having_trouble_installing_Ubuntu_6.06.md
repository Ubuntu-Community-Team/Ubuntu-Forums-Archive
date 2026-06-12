---
title: "Having trouble installing Ubuntu 6.06"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by jacatone on 2006-11-25
I created a 10 gig extended Primary partition using Partition Magic in order to install Ubuntu Linux
as a dual boot. To install Ubuntu I have to make this extended partition active but I'm at a loss as to how that's done. 

If I use the Ubuntu install it shows this extended partition as hda 2 within the hda 1 NTFS partition but I'm unsure how to proceed. I have the primary C drive (hda 1) and a logical second backup partition (hda 5). Keeps telling me I need a swap file as well. Thanks.

---

### Post by K.Mandla on 2006-11-25
Try un-partitioning that space. Guided partitioning (the default option) looks for the largest *unpartitioned* space.

---

