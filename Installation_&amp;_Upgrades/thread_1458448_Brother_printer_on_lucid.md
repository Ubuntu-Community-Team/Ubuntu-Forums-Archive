---
title: "Brother printer on lucid"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by gandalf2000 on 2010-04-20
I upgraded from Karmic to Lucid RC a couple of days ago and have been trying to work through a few problems since.  One of these problems is printing with my Brother DCP506CN printer which was working in Karmic.  However, I just can't seem to get it going in Lucid.  I have followed the Brother linux install procedure, which worked for the the last few Ubuntu releases, but not for this one it seems.  Any help would be much appreciated.

---

### Post by gandalf2000 on 2010-04-21
I ended up going back to Karmic and spent an hour on the Brother site trying to install drivers and didn't get it going.  I then went looking in Synaptic and found all the packages there.  Now it is working and never had so easy a printer install with linux before.  They are probably in Lucid as well just didn't think to look there as they have not been there before. :)

---

### Post by aaronsharpe on 2010-05-13
I am having trouble with this printer too in Lucid. No problems in older versions of ubuntu. I have tried both the drivers in synaptic and the drivers from the brother site with no luck at all.

---

### Post by gandalf2000 on 2010-05-15
Here is my reply to another post concerning a brother printer on lucid.  Guess I solved my own problem, If this works for you let me know and we will mark this as solved.

"I had the same issue and after banging around for awhile found a solution. If you go to System> Administration> Printing and double click your printer the "Printer Properties" GUI will come up. In the Device URI box of the "Settings" menu make sure that the network address is there. Mine had the printer name between the "lpd://NETWORK ADDRESS/binary_P1" After I changed the printer name to network address it was fixed."

---

