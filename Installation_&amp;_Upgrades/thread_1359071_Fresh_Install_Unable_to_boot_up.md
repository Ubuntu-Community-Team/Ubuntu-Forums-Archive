---
title: "Fresh Install Unable to boot up"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by newbie7 on 2009-12-19
Hello, does anybody know what this error means and how to fix it following fresh install thanks:

Error - biodisk write error, failed to boot default entries, press any key to continue.

---

### Post by alfax on 2009-12-23
I just had the same problem...
Anybody knows what it means and how to fix it?
HELP! :(

EDIT: this problem occursometimes  when I turn on my computer, other times It just don't does nothing. Obviously something is going on...

PD: Sorry if i have a bad English, I'm learning ;)

---

### Post by presence1960 on 2009-12-23
> **newbie7 said:**
> Hello, does anybody know what this error means and how to fix it following fresh install thanks:

Error - biodisk write error, failed to boot default entries, press any key to continue.

It is recommended that you not create dual threads on the same topic/problem. You already have a thread [here]("http://ubuntuforums.org/showthread.php?p=8531486#post8531486") about this problem.

I have been following your thread. It appears that you have a problem either with that 80 GB disk or your BIOS. To work around that why don't you resize your windows partition to create room for Ubuntu on sda since we know that disk works and is recognized by your BIOS.

To create room for Ubuntu from your Vista partition boot into Vista. Defrag Vista a couple of times. Go to control panel and turn off System Restore until Vista is shrunk. I would even turn off page file. Then use Vista's disk management utility to shrink Vista. When complete boot back into Vista and turn System Restore and page file back on. 

Now boot the Ubuntu Live CD and when you get to the partitioner window choose Install to the largest continuous free space. (free space on sda)

You do realize your comment about "wow ain't ubuntu great software" on your duplicate thread is the reason no one tried to help you any further. It is not Ubuntu's fault your 80 GB disk or BIOS will not work properly.

---

