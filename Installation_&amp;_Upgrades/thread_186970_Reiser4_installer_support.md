---
title: "Reiser4 installer support"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by mips on 2006-06-02
I've got the Dapper Installer up and running but I see no options to format my partitions as Reiser4  ???

Any ideas ?

---

### Post by gotaug on 2006-06-06
I used Synaptic and added gparted, the Gnome Partition Editor.  I also searched for Reiser4 and added everything that looked relevant.  I have selected all the "channels" under Settings|Repositories in Synaptic, and then reloaded (I reload before I search for new packages).

The Gnome Prtition Editor allowed me to create a Reiser4 partition, in free space on my disk.  Now I'm trying to figure out how to copy /root there and make Grub boot to that partition...  I'm new so any help would be appreciated.

---

