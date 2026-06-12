---
title: "No option to install beside Vista"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by canadianwriterman on 2010-07-06
I'm in the process of installing Lucid on my daughter's Vista machine, but there is no option in the partitioner to install it beside Vista. I'm a bit nervous about manually partitioning Vista. Any advice? Thanks!

---

### Post by oldfred on 2010-07-06
From within Vista use the control panel admin tools to resize the Vista partition to make free space. 

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

You can use gparted but be aware of this:
In the GPartEd or QTPartEd Partition Editors the tick-box **align to cylinders** must **NOT** be ticked because Windows 7 and Vista partitions usually start in sector 2048 instead of the normal standard sector 63.

Then you can install to the free space you have created.

---

### Post by canadianwriterman on 2010-07-07
Thanks for the guidance, OldFred. Seems odd to me that all the instructions for installing beside Windows indicate that it is an option during the partitioning stage. I wonder why it isn't in this case?

---

