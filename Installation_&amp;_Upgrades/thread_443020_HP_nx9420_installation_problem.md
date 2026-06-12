---
title: "HP nx9420 installation problem"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by immortalxak on 2007-05-14
i tryed to install ubuntu on HP nx9420 but when i wanted to startx he show me:

 XIO: Fatal IO ERROR 104 (connection reset by Peer) on XServer. ":0.0" After 0 Requests(0 known processed) with 0 Events Remaning.

I tryed to copy xorg.conf from knoppix (he boots successfuly) but it didn't work. Does anyone know how to solve this problem? 


Thanks in Advance

---

### Post by x64Jimbo on 2007-05-14
You should not need to run the "startx" command at all. The gdm should be handling your login, and X should be starting on boot without you having to tell it so. I believe the problem is deeper seated than you think. Tried reinstalling?

---

