---
title: "disc clone"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by MikeCyber on 2012-11-07
[I]Hi
I do right now a disc clone, as sda has faulty sectors:
dd if=/dev/sda of=/dev/sdb
Both discs are 1TB. How long should that take about?
Thanks

[/I]

---

### Post by Cheesemill on 2012-11-07
That depends on what type of disks you have and how they're connected.

If they are both internal then it will take several hours, if they are connected via USB then ***a lot*** longer.

---

### Post by MikeCyber on 2012-11-07
internal...somewhere on the net it said ~8 hours but hey after coming back it says input/output error after copying 400gb...sigh
  
I'll try later this:
sudo dd if=/dev/sdc of=/dev/sdb conv=noerror,sync

---

