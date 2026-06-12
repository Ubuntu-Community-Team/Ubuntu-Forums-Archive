---
title: "I need a little explaination of mount points."
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by Blue Eagle on 2007-02-19
I have only ever tried Knoppix before.

I have a new, blank 160GB hard drive, and an older 200GB one that I boot windows XP from.
I'm afraid I'll accidentally damage the windows installation on the 200GB drive.
I'm confident until I get the the installation screen that mentions mount points.
What do all the different "/" options mean? It lists The 2 partitions on the 160GB drive, but it also has my 200GB Windows XP hard drive set as something like "/sbc/media"

Please someone, help me understand what all this means.

---

### Post by Kateikyoushi on 2007-02-19
The mount points display the path to the mounted media.

For example after you boot your 2K partition can be found in /sbc/media.
It isn't going to hurt your existing filesystem unless you tick the format checkbox next to it.

---

