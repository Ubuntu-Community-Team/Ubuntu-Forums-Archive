---
title: "Partitioning for dual boot"
date: 2007-07-17
forum: Installation &amp; Upgrades
---

### Post by Riverglen on 2007-07-17
I would like to set up a dual boot on a laptop that is currently running Win XP.  I've read the info in the "appendix D" on how to do this and it looks pretty straightforward.  However, after defragmenting the drive, as recommended (using the XP defrag utility), the resulting disk usage map shows an isolated  block of used space way out to the right in the analysis window.  My concern is that I don't have any way to determine how much useable space there is beyond this last chunk and I don't know of a way to force the defragger to consolidate the space used by Windows at the beginning of the disk.  Will all of this shake out in the repartitioning process, or do I need to do some more clean-up before I attempt the install?

Also, does the recommended 10 gig partition represent a bare minimum, or more of a comfortably adequate allocation?  For now at least I don't expect to switch my computing life over to Ubuntu.  I'm more of a curious experimenter.  If/when I ever decide to get more serious about it, I probably would get another machine to run it on.

Larry

---

### Post by confused57 on 2007-07-17
Maybe some of the suggestions by Herman in this thread will help:
[http://ubuntuforums.org/showpost.php?p=3012574&postcount=9](http://ubuntuforums.org/showpost.php?p=3012574&postcount=9)

Partitioning links:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

---

### Post by Pumalite on 2007-07-17
I remember, I think, from long time ago, there was an option in diskeeper exactly for that. On the other hand, beware that that small partition is probably your 'rescue' partition ( you probably didn't get a CD from your vendor ). 10 GB is little, but enough. You could 'inspect' your hard drive with Gparted [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), and you could use to repartition if you wish.

---

### Post by dabl on 2007-07-17
First, I like to use the bootable GParted Live CD as a standalone disk viewer and partitioner, even though Ubuntu has GParted as a package.  You can download the ISO from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Second, my observation is that the root partition can get to 5GB fairly easily, and you DON'T want it getting full, so I would allow no less than 8GB for that. Then, a swap partition is mandatory, although mine never gets used, so you could probably be fine with 500MB for that.  The rest of the answer is, how much data space do you need -- that is your /home partition requirement.

HTH!  :)

---

### Post by Riverglen on 2007-07-17
Thankfully, this machine doesn't have a recovery partition.  Only the one XP partition. The "chunk" I was referring to is a piece of allocated file space that is isolated way above the rest of the space Windows is using, but not at the end of the disk.  For some reason the defrag didn't move it down to give me a nice contiguous block of free space that I can use to put the Ubuntu installation into.

---

### Post by dabl on 2007-07-17
Don't worry about that "Windows-centric" view of file placement on the drive -- that's just a visualization thing.  GParted will take care of that when you do the resizing -- your (properly backed-up) data will be fine.  :)

---

### Post by Pumalite on 2007-07-17
One of the links that confused57 gave you explains that 'chunk' and how to deal with it. I think.

---

### Post by confused57 on 2007-07-17
> **Pumalite said:**
> One of the links that confused57 gave you explains that 'chunk' and how to deal with it. I think.
Yes, that's why I provided a link to Herman's suggestions for efficient defragging.  I'm used to being ignored, even my wife & dog ignore me.

---

### Post by Pumalite on 2007-07-17
hahahaha! (lol)

---

### Post by Riverglen on 2007-07-17
I'm not really ignoring you.  I'm busily reading and digesting the stuff in the links you suggested.  Looks like they  will answer most of my questions.  Thanks for the tips.

Larry

---

### Post by confused57 on 2007-07-17
> **Riverglen said:**
> I'm not really ignoring you.  I'm busily reading and digesting the stuff in the links you suggested.  Looks like they  will answer most of my questions.  Thanks for the tips.

Larry
That's what I assumed...I was just trying to be humorous...hope it works OK.

---

