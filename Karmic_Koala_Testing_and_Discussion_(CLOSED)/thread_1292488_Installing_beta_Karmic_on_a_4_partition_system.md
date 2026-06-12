---
title: "Installing beta Karmic on a 4 partition system"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tom.swartz07 on 2009-10-15
Hi everyone,

Im in the process of getting my system upgraded for the Karmic release, and I would like to install karmic (9.10) side by side with my already present jaunty (9.04) and windows vista. I had tried to do a basic install, but apparently there is a 4 primary partition restriction on my system.

Here is what my drive looks like in gparted.
[IMG]http://lh4.ggpht.com/_tORug_uHNu4/StfcTAa4oDI/AAAAAAAAAIk/PeHbW3G6zpM/s800/Screenshot--dev-sda%20-%20GParted.png[/IMG]


I specifically upgraded my drive so that I would have space for the upgrades such as this, but it seems to be a lot more work than I expected because of this apparent limitation on number of partitions.


Would it be wise to extend the "parent" partition -/sda4- that holds all of the Linux partitions so that karmic could fit?

Could I possibly create a situation similar to the fix provided by the original Jaunty installation- could i create a partition and copy the Windows partitions inside and 'trick' it into seeing only 2 partitions?

---

### Post by beastrace91 on 2009-10-15
You do in fact need to make your "extended" partition larger - you can only have 4 primary partitions on any hard drive. Doing so *shouldn't* affect your Jaunty install at all - how ever as with any times messing with data partitions be sure to have any important data backed up ;)

~Jeff

---

### Post by tom.swartz07 on 2009-10-15
> **beastrace91 said:**
> You do in fact need to make your "extended" partition larger - you can only have 4 primary partitions on any hard drive. Doing so *shouldn't* affect your Jaunty install at all - how ever as with any times messing with data partitions be sure to have any important data backed up ;)

~Jeff

alrighty! ill bump it up.

You say it *shouldn't* affect it= what are some possible problems that will arise, other than a GRUB error or something?

What I plan to do is install side by side, then copy over any files I need, installers, etc. Then Ill delete the Jaunty partition, and move the Karmic into that former space.

Easy Peasy! 
GParted on a live cd should take care of the partitioning and moving everything. I do have everything backed up to an external though.

---

