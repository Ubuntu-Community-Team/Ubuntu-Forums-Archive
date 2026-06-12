---
title: "How well does Ubuntu operate with LABEL mounting?"
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2012-05-17
I'm looking at switching things over from using UUID= for selecting drives to mount in /etc/fstab, to LABEL= instead.  The reason I am doing this is because handling UUIDs is very awkward in my automated scripts.  Labels would be easier because I can just generate the right information, rather than have to keep track of information.  I was also considering generating the same UUID on each machine, but that has potential to cause problems, such as when taking a drive from one machine to another to recover files if the other one dies.  So I would use labels with the hostname and mount point (e.g. like "foobar-usr").  Then I would generate an /etc/fstab (again) so it uses labels instead of UUIDs.

The question I'm asking is if anyone has experience using LABEL= instead of UUID= to reference drives to be mounted in Ubuntu and can relate how well Ubuntu deals with it.

---

### Post by wilee-nilee on 2012-05-17
Not sure about labels I use /dev/sdaX rather then a UUID, not sure this helps.

---

### Post by Skaperen on 2012-05-18
> **wilee-nilee said:**
> Not sure about labels I use /dev/sdaX rather then a UUID, not sure this helps.
It can help somewhat.  At least half the issue, that nothing depends on using UUID, is resolved.

I'm just going to go ahead and make my installer set up with labels because they are deterministic giving a hostname and mount path, which I will make the labels from.  Now that I've found a partitioning program that lets me do things the way I want, I can go ahead and make the installer script.

---

### Post by diesch on 2012-05-18
Using LABEL should work as well as using UUID. Of course you have to make sure that your labels are unique enough.

---

### Post by Skaperen on 2012-05-27
> **diesch said:**
> Using LABEL should work as well as using UUID. Of course you have to make sure that your labels are unique enough.
My labels will be made from hostname with filesystem abbreviation appended.

---

