---
title: "[SOLVED] Getting RAID back after fresh install (7.10 -&amp;gt; 8.04)"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by NickZA on 2008-08-06
Hi folks

A few days ago I installed 7.10 from a CD I'd burnt a while back. I built a nicely working RAID-1 with this guide -- [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188).
I then messed things up a bit with Compiz etc. and decided to do a completely fresh install. I did that, and then did a live update to 8.04.

OK, now I want to get my RAID back and make sure it's working / synced. I added this line to my fstab, and commented  the two below it which were in by default from the fresh install:

Then mounted md0, and it appears to be working fine, at least, I can see files and folders, open text files etc. and it's working smoothly so I suspect no problems.

However when I go into gparted I get the little caution icon on both:
--the two drives that constitute the array (I think this is normal though once you make a RAID with them, i.e. they no longer have valid individual partition tables(?)
--the RAID itself, md0.

It's the second one I'm most concerned about. When I get properties on /dev/md0 in gparted it says
```

warning:
e2label: No such file or directory while trying to open /dev/md0p1
Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.
.
.
.
Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.

```

Any ideas? Am I good to go? Did I just miss something when trying to resurrect the array?

TIA,

-Nick

---

### Post by tamoneya on 2008-08-06
I think you forgot a link.  which guide did you use originally?

Also try this command:```
sudo apt-get install mdadm
sudo mdadm --scan --assemble

```

---

### Post by NickZA on 2008-08-07
Oops, that was [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)

Thanks for pointing that out!

I tried
```
sudo mdadm --scan --assemble
```

..Before I had refreshed my fstab with the md0 line as described above. It came back with complaints, although I can't recall what they were.

But I sort of assumed one has to put the fstab lines in again before one can do anything else(?), so maybe if I'd done this:

1. change /etc/fstab
2. sudo mdadm --scan --assemble
3. mount the array

instead of only steps 1 and 3 (as I have done), it might have worked better. Perhaps I can try when I get home. However I already issued a write operation on the disk last night so if anything is going to be messed up it will be after that. (Doesn't seem to be though but I'm not sure how to check thoroughly.)

---

### Post by NickZA on 2008-08-09
bump! Can anyone tell me what those errors mean and if they are anything to be concerned about?

---

### Post by NickZA on 2008-08-09
SOLVED: The caution icon and it's associated warnings appear to always display in gparted when you have created a functional soft RAID using mdadm.
So nothing to worry about. (I tested by deleting the old array completely and creating a new one.) :popcorn:

---

