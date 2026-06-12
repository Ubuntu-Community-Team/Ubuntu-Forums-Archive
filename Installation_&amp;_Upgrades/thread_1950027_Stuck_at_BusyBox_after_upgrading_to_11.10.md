---
title: "Stuck at BusyBox after upgrading to 11.10"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by webcomm on 2012-03-31
I have Windows XP / Ubuntu (wubi) on one partition.  I created a *new* partition and installed Natty on the new partition.  I was able to boot into the new partition with no problem.  I then tried upgrading Ubuntu on the new partition from Natty to Oneiric.  The upgrade seemed to go smoothly, but when I rebooted I could no longer boot into the new partition.  I get stuck at BusyBox.  

I can still boot into the old partition with no problem.  I can boot into Win XP and run chkdsk /r and see that the disk is clean.  No problems.  I can also boot into Ubuntu (wubi) on the Windows partition.  So, it appears there is nothing wrong with the disk.  

How do I get past BusyBox in the new partition?  I see there are many other similar threads, but some threads end with no resolution, some are quite old, and some end with the poster realizing their disk is damaged.  My disk appears to be fine.  In fact I'm typing this in the wubi install on the Windows partition. 

To summarize, I have...

[LIST]
[*]Win XP / Ubuntu on sda2.  The Ubuntu version is Oneiric.  No disk problems.  I can boot into Win XP and Oneiric with no problem on sda2.
[*]I created a new partition (sda3) and there I installed Natty.  It worked fine.  Then I upgraded that install to Oneiric and now am getting stuck at BusyBox when I try to boot into sda3.
[/LIST]
Suggestions?  Thank you

---

