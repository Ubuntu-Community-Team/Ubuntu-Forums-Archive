---
title: "need help moving &amp; consolidating file systems"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by akahige on 2008-11-05
I've got an issue with file system space on my Hardy system. It's been going on for awhile, and until now, I've been able to work around the limitations. Now, I need to do something about it, and I need some advice and assistance to make sure I don't trash my system.

/var -- while totally functional -- doesn't have enough space on it to download the packages for an Ibex upgrade.

/ is a little more than 10% full, so my thought is that the best way to deal with this issue is to move /var onto the / file system, then delete the current /var fs and grow / out to include the space left over. (GParted should be able to handle this.)

The file systems are all XFS -- which can't be shrunk, only grown -- otherwise, I would just shrink / and grow /var.

Consolidating the / and /var file systems sounds basic in concept -- and it might well be -- but practices change and I've gotten some bad advice over the years, so I want to make sure I don't do anything that will cause me grief later.

Can anybody give me a step by step of what I need to do...?

Thanks!

---

