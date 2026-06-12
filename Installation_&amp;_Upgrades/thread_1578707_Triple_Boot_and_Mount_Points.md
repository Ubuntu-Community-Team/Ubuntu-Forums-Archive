---
title: "Triple Boot and Mount Points"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by brother jon on 2010-09-20
Thinking about adding Kubuntu (maybe Ubuntu) 10.04 to an already dual-boot system - PCLinux and Vista.

HDA is windows.
HDB has swap, /, and /home partitions, plus another swap, a 20GB partition, a 50GB partition, and 70GB unallocated.
The extra swap, 20, and 50GB parts are there from an old tryout of something else, with no mount points defined.

I'm pretty sure the bootloader (Grub) references partition IDs (e.g. hdb1, hdb2, etc.), not mount points, but my question is,
will having two / and two /home partitions on the same HD confuse things?

Sorry; it's been a while since I installed anything, and am just making sure.  Tried to go to the documentation
site, but can't get there right now- server tied up or something.

TIA

---

