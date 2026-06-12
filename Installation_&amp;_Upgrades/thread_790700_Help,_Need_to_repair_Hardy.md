---
title: "Help, Need to repair Hardy"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by cherylholmes on 2008-05-11
I fried my install of Hardy Heron by deleting (removing) a bunch of stuff in Synaptic.  Lost System>Applications, and lost a bunch of stuff under Applications including Add/Remove.  Still have terminal but no synaptic either.

My HP Officejet G85 hasn't worked in Hardy so I thought maybe it was CUPS since when I would try to print the popup screen said CUPS and PDF..the doc I was trying to print (for Mom, Mother's Day) is not a PDF so I thought if I removed all that CUPS crap, it might print.  Well, now I can't even open any documents either.

Is there a way to "REPAIR" Hardy without doing a complete reload?  I have the CD.  Thought maybe it might be repairable like Windows can be repaired...thanks cheryl

---

### Post by lswest on 2008-05-11
you can try doing this:
```
sudo apt-get install --reinstall ubuntu-desktop
``` in the terminal, that should get the majority re-installed.

---

