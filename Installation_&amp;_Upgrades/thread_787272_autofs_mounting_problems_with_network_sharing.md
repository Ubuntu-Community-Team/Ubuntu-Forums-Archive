---
title: "autofs mounting problems with network sharing"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by Ancientmtk on 2008-05-08
I have a server running on redhat ws3 and a new ubuntu 8 client that im trying to get to mount server drives. The ubuntu box can ping the server and i can manually mount the server drives by doing

mount server:/export/disk1 /shared

but when i utilize autofs, its not working.
The daemon.log file says something about "automount: failed to mount /shared/.Trash" or something along that line.

What is wrong here, the autofs or maybe the config files?

---

