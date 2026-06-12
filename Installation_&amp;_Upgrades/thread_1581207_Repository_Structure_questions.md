---
title: "Repository Structure questions"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by website.reader3 on 2010-09-24
[My apologies if this isn't the correct forum, I tried to pick the closest one]

Is it better to follow the traditional Ubuntu mirror archive folder structures using the "debmirror" command when creating a local repository or rather use a flat folder and tossing all the .deb files into it? (as suggested by the 2nd tutorial listed below)

There are two instruction manuals I am looking at:

[http://ubuntuforums.org/showthread.php?t=352460&highlight=mirror+archive](http://ubuntuforums.org/showthread.php?t=352460&highlight=mirror+archive)

and

[http://ubuntuforums.org/showthread.php?t=1090731](http://ubuntuforums.org/showthread.php?t=1090731)

and I am inclined to the mirror structure.

Unfortunately I lost over 200 gigs+ of data the last two days, believing that debmirror was an incremental command and would add to the local repository, only to find to my dismay that it clobbered any previous data.

Indiscriminantly using the rsync command led to it trying to copy over 500 gigs+ of data, fortunately I caught that over-reliance early.

My goal is to create a local repository on a server, then point the client machines on my LAN to it for upgrades or install of needed programs.

---

