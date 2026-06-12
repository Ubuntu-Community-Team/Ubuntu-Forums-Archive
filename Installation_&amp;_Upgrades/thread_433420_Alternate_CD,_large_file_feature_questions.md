---
title: "Alternate CD, large file feature questions"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by ShirishAg75 on 2007-05-04
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/bugs/99303](https://launchpad.net/bugs/99303) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Hi all,
       Although I've installed feisty without issues but when I use the large file feature while manually partitioning with debain-installer.   

   I reported the issue in launchpad and 
[QUOTE=Colinwatson]
I suppose anything's possible, but it seems unlikely that largefile
could be involved unless you're running close to the edge of disk space
requirements.[/QUOTE]

Now what does he mean by that. I have put up the following screenies by pushing the same through a VM. Thankfully, this is something which happens again & again. 

[IMG]http://img264.imageshack.us/img264/3908/bootparameter1ag0.png[/IMG]

[IMG]http://img175.imageshack.us/img175/2606/hddmanualpartition2bp2.png[/IMG]

[IMG]http://img70.imageshack.us/img70/4886/packageinstallationerrogf5.png[/IMG]

[IMG]http://img175.imageshack.us/img175/1961/vt4errorlogpw8.png[/IMG]

[IMG]http://img511.imageshack.us/img511/586/partitionsetupla0.png[/IMG]

 Now I have few questions, starting from is there something which I haven't looked into ? What is this 5% Reserved blocks ? Are these reserved out of the partitions I make or do I need to leave that much space free (no partitioning) ? So for e.g. if I have a 76 GiB hdd, then I should partition 72 GiB  for my / , /home & swap & leave the remaining unpartitioned or what?

      Also what does Mr. Colin means when he says [QUOTE=Colin Watson]I suppose anything's possible, but it seems unlikely that largefile
could be involved unless you're running close to the edge of disk space
requirements.[/QUOTE]

      Looking forward for suggestions, additions, clarifications on the above issue. Cheers!

---

### Post by zvacet on 2007-05-05
Why didn´t you select** Finish partitioning and write changes to disc**?I ask this because it look like you did finish partitioning.

---

### Post by ShirishAg75 on 2007-05-05
I did write changes to disc. Ok I did get some more info. on IRC ubuntuforums channel by John Dong, apparently if u use largefile that means 1 MB per inode. As per the explanation given to me it means 1 single file and the base install is something to the tune of 1,115 or about files. Which means I should have had 100 GB + hdd if I want to use largefile. Hence my base-install didn't work. 
      In fact he also commented on the bug report [https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/99303](https://bugs.launchpad.net/ubuntu/+source/pkgsel/+bug/99303) which makes thing much more clearer.

---

