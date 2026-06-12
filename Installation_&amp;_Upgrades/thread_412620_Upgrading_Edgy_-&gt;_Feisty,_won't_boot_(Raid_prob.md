---
title: "Upgrading Edgy -&gt; Feisty, won't boot (Raid problem)"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by zooounds on 2007-04-18
Hi!

After running

update-manager -c 

and upgrading my Edgy to Feisty my system can't start anymore.

I think it has something to do with the fact that I have  / och softraid (1) /dev/md1, swap on md0 and home on md2.

After the upgrade the update-manager left on empty window opened. I closed this after about half on hour and rebooted. 

At boot, my computer always stalls when mounting /

PLEASE HELP!

What could I do?

---

### Post by Salpiche on 2007-04-18
I have the same problem and I am not using raid. Everything is fine and after upgrade if /when restart it would give me just the cursor on the top left corner of the screen.

---

### Post by zooounds on 2007-04-18
I have tested with an older kernel I have installed now.

Everything works (including activating md0 and md1) but it stops at activating LVM (That is on md2)

---

### Post by zooounds on 2007-04-18
addpending break=mount when booting and running

mdadm --assemble --scan --auto=yes

says something like:

mdadm: Unknown keyword hexhexhex:hexhexHex:hexHexHex:hexhexhex

3 times

And then "No arrays found in config file"

---

### Post by mindaslab on 2007-04-18
Why not trying install 7.04 by creating a new partition of 3 GB. Then log on to that installation and try retriving your files. I am not a coputer guru, but just key in the idea that struck me.

Regards
A.K.Karthikeyan :guitar:

---

