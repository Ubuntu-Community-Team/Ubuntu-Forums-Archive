---
title: "HELP!! Want to remove old 7.10 and do clean reinstall !!"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by calldrin on 2007-11-08
I'm running a dual boot XP and 7.10 and I want to keep my XP and remove all traces of 7.10.
Then I want to reinstall 7.10.(my old CD had errors)
Using the "live CD" I have a problem understanding how to remove the old system and then install the new version.
The Gparted always show the old partitions with the sizes "which I want to change but seems that it won't let me change the ex3 and the swap will only go to 8Mb in size.

If this seems confusing to read, I'm sorry, BUT I'm having a hard time getting a simple step by step answer... As you can tell I'm very new to Linux ;-(

Chuck

PS: I have read several posts about this but I still can't seem to get the  right answer !

---

### Post by bulldog on 2007-11-08
Just boot windows then and remove your linux partitions.
Don't create new ones,left the space unallocated.
Boot your ubuntu cd and create new partitions in the free space.

---

### Post by Irony on 2007-11-08
Like Bulldog says; boot into windows go to disk management and unallocate the the linux partitions.

I would then merge the unallocated partitions (maybe windows does it automatically on unallocating adjacent partitions, I can't remember).

Then pop in the ubuntu CD, now shutdown (don't restart). Now boot up and do an autoinstall to the freespace.

---

### Post by calldrin on 2007-11-08
Thanks for the help.
I booted into G-Parted live CD and was able to delete my old partitions from there and did a new install:-)

Chuck

---

