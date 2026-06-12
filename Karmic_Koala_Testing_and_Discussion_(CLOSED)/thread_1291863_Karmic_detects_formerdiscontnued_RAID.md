---
title: "Karmic detects former/discontnued RAID"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bugritall on 2009-10-15
I have four hard drives, a 150GB and three 500GB, all sata and all WD.

XP is installed on the 150GB drive, sda1, Jaunty is on sdb5 and I have recently installed Karmic Beta on sda9. All three operating systems are co-existing happily.

However, Karmic won't recognise two of my 500GB drives, sdc and sdd.

These two  were previously used in a RAID 0 configuration which I have now discontinued.

Both XP and Jaunty are content that these drives are now independent entities.
 
I suspect that Karmic believes that they are still a RAID and, because it later discovers that they are not, it just gives up on them.

If I'm right, how do I tell Karmic to forget about RAID?
- alternatively -
How can I eradicate  "RAIDification" on the drives?

Incidentally, the Karmic live CD doesn't recognise the (former) RAID drives either.

---

### Post by bugritall on 2009-10-16
I was right to suspect RAID. Following advice I found [here]("http://forums.anandtech.com/messageview.aspx?catid=34&threadid=2215469&enterthread=y&STARTPAGE=1"), Karmic had no more problems with the former RAID drives after I re-initialsed them with:
```
dd if=/dev/zero of=/dev/sdc count=1 bs=1024000 
dd if=/dev/zero of=/dev/sdd count=1 bs=1024000
```I did have to shunt an awful lot of data around first, though.

---

