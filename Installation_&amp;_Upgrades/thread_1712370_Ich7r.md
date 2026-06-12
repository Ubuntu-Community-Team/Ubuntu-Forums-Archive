---
title: "Ich7r"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by nariub on 2011-03-22
I discovered something the other day and thought I would share.
 
I have a few Dell Dimension E510s, since April 2006.
Upgraded to 4G of RAM and it only sees 3.2G, apparently a BIOS issue.
 
It has an ICH7R Raid controller on the Motherboard which originally came with two 160G harddrives in a RAID1 Mirror.
 
I have used Ubuntu 10.04 and 10.10 on these boxes for a while.
 
...  OK here's the thing
I wanted to put two 2T harddrives in, I wanted to run RAID1 Mirroring, and end up with a single installation with Ubuntu 10.10, no dualbooting or anything.
 
She would not cooperate, install would go fine and when she rebooted, it would time out awaiting root.   
 
Beat my head on the wall for a few days.   Then found that the ICH7R did not like 2T arrays, even though it created them just fine.  Also found that Intel has updated this but Dell stopped releasing BIOS updates for my old box prior to the Intel update.  
 
I got it to work by splitting my RAID1
I created two RAID1 Mirrors,  
OS = 160G
HOME = remainder of the 2T
 
and the ICH7R would only let me create a maximum of two arrays.
 
Whole 2T still in the RAID1 Mirror, but in two pieces.   They are presented to the installer as two harddrives, which probably gets it around the old MBR/GPT thing too.
I haven't checked which it is using right now.
 
Thought it might be helpful if anyone else was considering beating their head against a wall over something like this.

---

