---
title: "How do I disable/remove device mapper?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jbirdjavi on 2009-10-24
I just upgraded to 9.10 on my mythbuntu system, and quickly found that something was amiss when it refused to boot up.  After a lot of searching and panic mode setting in, I finally figured out that device mapper was taking control of my hard drives before they could be properly mounted the way I had them set up (I have two 400GB drives with a software RAID 0 partition across 385GB of each drive for storing recordings.  The first 15GB of one drive is where the system resides, and the 15GB on the other drive is swap (yeah I know I don't need that much swap, but what else was I going to do with it?)).

All that said, I finally figured out I could boot into my system by adding "nodmraid" as a kernel boot parameter.  At the moment I have to manually put that in every time I boot up the machine.  What's the best way to go about disabling device mapper?  Is there a way to totally remove it from the system?  Or would it be better to get grub to add the "nodmraid" option permanently?  (Keeping in mind that I'd want it automatically added to new kernel updates when they come around.)

---

