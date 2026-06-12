---
title: "Problem Upgrade from fiesty to gutsy (gzip returned error code 1)"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by sulemankm on 2007-10-20
Hi,

I've tried to upgrade several time over the last two days but every time I get this error during the "Modifying Software Channels" step.

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)

I've seen other similar threads with similar problem but couldn't find a satisfactory solution for the problem.

I also felt it necessary to report this error so that it is fixed in near future.

Regards.

---

### Post by Ba66e77 on 2007-10-21
See this thread: [http://ubuntuforums.org/showthread.php?t=582512&highlight=Sub-process+gzip+returned+an+error+code](http://ubuntuforums.org/showthread.php?t=582512&highlight=Sub-process+gzip+returned+an+error+code)

---

### Post by sulemankm on 2007-10-22
Thanks,

I solved the problem by replacing http:// with ftp:// in the sources.list file for the main repositories line.

But now I have another problem in the installation step. I have posted this problem is another thread.

---

### Post by sulemankm on 2007-10-22
Here is the link to the thread for my other problem.

[http://ubuntuforums.org/showthread.php?t=586499](http://ubuntuforums.org/showthread.php?t=586499)

---

