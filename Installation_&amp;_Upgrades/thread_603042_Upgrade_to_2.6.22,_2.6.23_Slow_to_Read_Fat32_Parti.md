---
title: "Upgrade to 2.6.22, 2.6.23 Slow to Read Fat32 Partitions"
date: 2007-11-04
forum: Installation &amp; Upgrades
---

### Post by cb474 on 2007-11-04
When I upgraded to Gutsy, suddenly my system became very slow to read Fat32 partitions. When I go to access those partitions in Nautilus, it takes ten seconds to just show the file structure of the partition (I timed it). The second time I go to the same partition it's quick, as if the system knows the file structure now. But that only lasts for a while and then the slow ten second read will happen again.

Ext3 partitions come up quickly in a second or so even the first time.

I did not see this behavior in Feisty. However I did notice it when I tried upgrading to the 2.6.23 kernel in Feisty and I also noticed it when I tried installing Debian Lenny, with the 2.6.22 kernel.

What's going on? Is there any solution to this?

---

### Post by ofb on 2007-11-04
Might be related to this
[http://ubuntuforums.org/showthread.php?t=598073](http://ubuntuforums.org/showthread.php?t=598073)

There are a number of problems right now that may have something to do with IDE detection in the new kernel. I haven't been able to make head&tail of it yet.

Mainly my hope is the devs will be able to decipher the various bug reports fairly soon and get a fix in the pipeline. What we've got right now is dubious hacks and unanswered threads.

---

