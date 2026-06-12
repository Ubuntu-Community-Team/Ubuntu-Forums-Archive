---
title: "Reinstall Ubuntu with Existing Home Partition?"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by Redalien0304 on 2013-04-17
Want to Reinstall Ubuntu 12.04 with my Existing Home Partition? Keeping all my Stuff om Home partition safe. I will do Backup of Home to make sure that everything is Safe. From what Understand the Process is to Select Manual Partition in Install & select Home Partition But not to Format it? Am i Right? Can 2 Root Partitions use the same Home Partition? Sorry if i am Re-posting a question might have already been answered. Any help is Appreciated Thanks

---

### Post by oldfred on 2013-04-17
Yes, you use Something Else or manual partitioning and choose the existing /home partition but DO NOT format it.

It is primarily to do an upgrade. Newer software may have settings that older versions do not recognize. Some with same version or very similar versions have shared /home, but most use a different userID or name so you do not have the same data nor settings. 

I do not share /home but have separate data partitions which I do share. Then I do not have to worry about settings from one system changing another system.

---

