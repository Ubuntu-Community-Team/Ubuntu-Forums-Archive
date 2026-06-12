---
title: "Lesson learned in upgrading/installing"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by gjtoth on 2007-05-20
I just finished losing EVERYTHING I didn't make current backups of.  Some stuff is gone for good because I *assumed* files on peripheral drives would remain untouched during an upgrade.  I was dumb enough to assume that my /home directory was safe, too.  It seems that when one does a manual selection of partitions to use, Linux (don't know if it's peculiar to Ubuntu or not) automatically formats ANY DRIVE YOU SELECT TO USE.

Guess I got a little to cocky, eh?  I'm glad I had some backups to some relatively important stuff.  Boy, do I feel stupid.

---

### Post by zvacet on 2007-05-20
No it is not.You have to tell installer to format partition or not.

---

### Post by gjtoth on 2007-05-21
> **zvacet said:**
> No it is not.You have to tell installer to format partition or not.

Well, I beg to differ.  All I did was select the partitions for use.  Period.  NOTHING was mentioned about formatting anything.  Had there been, you can bet I certainly would have aborted and looked for alternatives.

---

### Post by abcStu on 2007-05-21
I had somewhat similar experience.  Ubuntu installer seems keen to assume agreement and may in fact not be hearing user input, particularly since the hardware detection may not be 100%, but seems to be presumed so.  I found that the partitioner step was wired to prefer automatic.  I would submit the default ought to be manual.  Moreover, the entire device choices throw you into a "we'll reformat the entire device" mode, which you had better catch before it happens.
But, for manual mode, it does not presume to format partitions with filesystems, even swap.  And that's good.

---

