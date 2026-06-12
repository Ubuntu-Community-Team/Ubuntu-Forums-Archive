---
title: "Error creating partition"
date: 2011-04-19
forum: Installation &amp; Upgrades
---

### Post by hardrail on 2011-04-19
Hello. 

I'm trying to install Ubuntu Desktop 10.10 alongside a Windows XP installation. I get to the point where I move the slider to allocate space between XP and Ubuntu and when I select the create partition button it just simply says "Failed to create partition" and the installation aborts. 

XP will run check disk upon the next restart and I'm back to square one. 

Does anyone know what might be the cause of this?

I really appreciate anyone taking the time to help out.

---

### Post by ajgreeny on 2011-04-19
> **hardrail said:**
> Hello. 

I'm trying to install Ubuntu Desktop 10.10 alongside a Windows XP installation. I get to the point where I move the slider to allocate space between XP and Ubuntu and when I select the create partition button it just simply says "Failed to create partition" and the installation aborts. 

XP will run check disk upon the next restart and I'm back to square one. 

Does anyone know what might be the cause of this?

I really appreciate anyone taking the time to help out.
Not totally sure what causes the problem, but I do know that the 10.10 installer can wipe a windows install even when you believe that you have asked for the two to be put alongside one another.

The (more) failsafe way is to defrag windows a couple of times, then shrink your windows XP partition with ubuntu live CD, using System ->Administration ->Gparted.   Then go on to install ubuntu, but choose manual partitioning at the ubuntu installer's partitioning page, and within the free space, make new partitions.

---

### Post by hardrail on 2011-04-20
Thanks a lot for the reply. That makes sense to do it that way. I'll give it a shot.

---

### Post by Hedgehog1 on 2011-04-20
This can be caused by your computer already having all 4 primary partitions filled.

I you would like us to have a look at the current computer layout and help you in this area, please do this-

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

