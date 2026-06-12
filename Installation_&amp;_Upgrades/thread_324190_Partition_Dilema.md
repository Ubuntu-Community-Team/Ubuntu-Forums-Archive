---
title: "Partition Dilema"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by AlanRogers on 2006-12-23
I'm running Ubuntu 6.06 on a 400MHz, 512MB, 8GB machine with separate partitions for root, home and usr but, as you can see, usr is full! :blush:
Output from System Monitor:[LIST]
[*]Device   Directory   Total   Free
[*]/dev/hda1   /   3.0GB   2.6GB
[*]/dev/hda6   /home   2.2GB   2.0GB
[*]/dev/hda7   /usr   2.2GB   423.6MB
[/LIST]I've obviously made /usr too small but what minimum sizes should each partition be anyway? Also, what's my best course of remedy?
[LIST=1]
[*]Move /usr to /, delete partition and resize /
[*]Resize / and resize /usr to grant more space to /usr
[*]Reinstall - nothing much on here yet anyway
[/LIST]
Thanks in advance for the help. I've downloaded qtparted from sourceforge in preparation/anticipation.

---

### Post by cilynx on 2006-12-25
I hate to say it, but in your case I would simply dump everything down to a single partition unless you --really-- have a reason to span partitions.  Spontanious hardware failure is pretty rare these days.  Split partitions aren't really necessary unless you're on a mission critical system.  (As a network consultant, I alway partition my servers, and never partition my desktop boxen.)

Boot the Dapper install CD, you can do everything you need from there w/o your system live.

Move /usr to /, look into the options on mv and cp.  You want to preserve everything possible.  I believe they call it "archiving".
Fire up gParted.  Free hda7 and shuffle to give the space to /
This will take a long time.  Exit gParted
Move /home to /,
Fire up gParted, free hda6 and the container partition and give the space to /

That's what I would do.  If you're dead set on keeping your partitions, it's totally possible.  I still recommend using the Dapper install CD and gParted however.

---

