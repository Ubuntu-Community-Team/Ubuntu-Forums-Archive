---
title: "Labeling Hot Swap Sata Drives"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by bricktop on 2007-09-21
Hi Guys,

Not sure if this is the right place to be asking this, sorry if it's not.

Anyways here is what I want to achieve.

I have a 4U server with 8, 500GB Sata drives in hot swap bays. these are running of 2, 4 port sunix sata controller cards. The cards and all the drives are properly recognized in Ubuntu 7.04 CLI.

**I would like to achieve the following:**
[LIST=1]
[*]Make the 8 Sata drives hot swappable and be able to remove them whenever they are not mounted without having to power them down first
[*]Label all the drives so thet when they are removed and then returned into a different drive bay they are recognized as the same drive with the original mount point, viz( label dev/sdd1 as drive1 so when it gets removed and then replaced in say drive4's bay it still gets recognized and mounted as drive1)
[/LIST]

Help is humbly requested, the machine is going to be used as a hard drive based backup server and the 8 drives are going to be used as off site backups which will be rotated weekly.

thanks

---

### Post by MrHippocampus on 2007-09-21
Im not sure on the first point (I have no experience in this area).

On the second point what you can do is write custom udev rules for the drives. A nice tutorial which should get you started on this is in a thread already on the forums [here]("http://ubuntuforums.org/showthread.php?t=168221").

---

