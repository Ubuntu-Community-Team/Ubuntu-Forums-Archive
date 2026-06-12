---
title: "Kernel upgrade from Dapper 6.06"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by fizikz on 2008-03-09
Is there a reasonably easy way to upgrade the kernel in Ubuntu Dapper 6.06 to something more recent than 2.6.18? Currently, I have 2.6.15.51, but I have a few reasons why I would like a more recent kernel:

-try to get my laptop's integrated webcam+mic to work. The driver requires minimum 2.6.18
-to get ntfs support. The ntfs-3g driver also needs more recent kernel.
-hope to fix problem of no sound after hibernate or standby
-hope to fix random skips when playing audio

My objective is to solve most of the points listed above, and a kernel upgrade seems to be the path to take. Can this be done relatively painlessly? I'd really appreciate to know how.

---

### Post by zvacet on 2008-03-09
Read [this](http://ubuntuforums.org/showthread.php?t=56835&highlight=kernel) [this](http://ubuntuforums.org/showthread.php?t=43065&highlight=kernel) and [this.](http://ubuntuforums.org/showthread.php?t=311158&highlight=kernel)

---

### Post by banewman on 2008-03-09
If you wait till next month the next lts release will be available. That should address your issues.
This post -
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
will let you now how to get a later kernel for you're system.
:)

---

### Post by fizikz on 2008-03-09
Thanks! Those threads are very useful, especially the Master Kernel Thread. KernelCheck also looks promising. But I still have a few questions:

1) I know the new LTS version of Ubuntu is coming out this spring. Will I be able to upgrade my current installation, keeping my files and configuration, or will it require a clean install. I've read that it is generally better and less hassle-prone to do clean installs of new versions. I've grown accustomed to 6.06 and as long as I can install the features and programs I want, I don't really see the need to get a new version of Ubuntu.

2) How much space will the new kernel installation require? I'm running low on available disk space on the current partition (~530MB available) and something tells me it wouldn't be good to run out of space in the middle of a kernel compilation.

3) Does the new kernel (2.6.24) have built in support read/write for NTFS, or do I still need to get the ntfs-3g driver?

4) Most of the threads on kernel upgrades don't mention much on what options to select for configuring/optimizing the new kernel. Would the default options usually work? 

I think those are all the questions for now... I hope to be running a new kernel soon! Thanks again for the help. :)

---

