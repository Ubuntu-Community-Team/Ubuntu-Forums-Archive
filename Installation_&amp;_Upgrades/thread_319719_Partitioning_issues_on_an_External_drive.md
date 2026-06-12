---
title: "Partitioning issues on an External drive"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by PietreWitobi on 2006-12-16
So I have this friend, who just got a 120 gig external.  He decides "My computer boots from USB... I'll make a Linux box!  Pietre, you run Ubuntu and still have your 6.06 LiveCD - you can help!"  I'm more than happy to help, but here's the thing.  I boot to the Live CD, and I say to him (how are we going to do this) and we decide as follows.  4 gig Swap, 5 gig Ubuntu(ext3), and 110 gig /home (Fat32).  So we do so, and I come to find that hey - I can't resize his old partition.  "No problem, " I say, "We'll just back up the installers you already have there onto your windows desktop... and create all new partitions!"  So I do.  Then it tells me that the partitioning fails because the "disc is busy" so I say, unmount it!  we do so by right clicking the Icon on the desktop and clicking "eject".  Then we proceed to attempt again.  Half-way through the partitioning, it opens up nautilus, browsing the damn drive, and gives me the same freaking error message.

I was thinking about unmounting it via the terminal... but I can't figure out the device path.  I know that the Partitioner sees it as sda1...

Is there something I'm missing, or am I on the right track with a little misdirection?

---

### Post by PietreWitobi on 2006-12-17
BUMP

Anyone?

---

