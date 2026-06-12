---
title: "Instructions for dual boot"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by pcostanza on 2007-03-08
I've seen a few posts with info on dual booting but I would like more info on the partition side of the install.
I have Vista installed (yuck so far!) and have a separate hard drive that I partitioned to 40GB.  I get to the point of the install asking me to select a root (/) but I'm not sure what I'm doing at this point and keep getting an error stating I have more than 1 partition selected.
As I don't see any info on this in the docs I've looked at, where can I find this specific info?

Did you guess I'm a newb yet? :) 
Thanks much

---

### Post by Kateikyoushi on 2007-03-08
In a nutshell
You need to make 2 partitions a 1GB swap and a bigger at least 7GB for /.
Set the mount point as / for the bigger linux partition and as swap for the smaller.
Your windows partition can be mounted in /media/...

I recommend toread this guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by Motoxrdude on 2007-03-09
> **pcostanza said:**
> I've seen a few posts with info on dual booting but I would like more info on the partition side of the install.
I have Vista installed (yuck so far!) and have a separate hard drive that I partitioned to 40GB.  I get to the point of the install asking me to select a root (/) but I'm not sure what I'm doing at this point and keep getting an error stating I have more than 1 partition selected.
As I don't see any info on this in the docs I've looked at, where can I find this specific info?

Did you guess I'm a newb yet? :) 
Thanks much

All you have to do is create two partitions for ubuntu, an ext3 partition and a swap partition. The swap partition should be around 512mb-1gb and the ext3 partition should be at least 8gb but can be as big as you want
Well, when you are at this screen, you have to tell ubuntu where to mount each partition/hard drive.
[IMG]http://img.photobucket.com/albums/v716/dragonwake13/MountPoints.jpg[/IMG]
The ext3 partition should be mounted as "/" and the swap as "swap". The vista partition should be left at default.
Hope this helps.

---

### Post by pcostanza on 2007-03-09
So making a 40GB partition is not enough?  I need to make a smaller, 2nd partition?
OK, can do.  Thanks for all the very quick replies.

---

### Post by pcostanza on 2007-03-09
Got it installed just fine and now I have much, much learning to do.
Thanks again for your invaluable info.

Paul

---

### Post by zvacet on 2007-03-10
[http://ubuntuforums.org/showthread.php?t=380713]("http://ubuntuforums.org/showthread.php?t=380713")

---

