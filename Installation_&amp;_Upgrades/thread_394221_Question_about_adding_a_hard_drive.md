---
title: "Question about adding a hard drive"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by hansoffate on 2007-03-26
Currently this is my partition scheme for my mythtv/storage server.

hda1       /      10gb    ext3
hda2      swap 1gb (should have increased it to 2)
hda3      /var/lib  about 170gbs for recordings      XFS
hdb1      /share     250gb     ext3     (a share for windows computers to access)

I want to add more storage for /var/lib so I can store more recordings.  I want to buy a SATA drive  (or 2 and raid them) and add it to this setup so I have more recording space.  

Someone suggested LVM.  How would I do this?

Thanks 
-Hans

---

### Post by hansoffate on 2007-03-28
bump

---

### Post by hansoffate on 2007-03-29
Bump

---

### Post by hansoffate on 2007-03-29
Bump?  Should  I just let this topic go?

---

### Post by Eric the Grey on 2007-03-29
Well, Hans, I'll bump this for you once...

I actually came here looking for exactly this answer, although in my case, I've not yet built my Myth box.

In my case, I will be starting out with an older Dell that currently has a 20 gig drive as it's primary, and a 60 gig secondary drive.  I will want to add another drive to it later on, when I have the funds to purchase one.

I too have seen that LVM is the tool to use, but I've never used it, and the guides here don't go into it at all.  This machine has no RAID support, and I think that is part of what LVM does.

So how easy is it to add a new hard drive and configure it to work with Myth.  In my case, I will probably be replacing the 60 gig with a 300gig and making the larger drive the place for recordings to be stored, possibly allocating the 60 gig for music and other media.


:cool: Eric the Grey

---

