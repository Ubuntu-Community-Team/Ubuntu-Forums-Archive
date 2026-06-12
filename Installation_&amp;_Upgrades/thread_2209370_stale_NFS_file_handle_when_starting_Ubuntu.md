---
title: "stale NFS file handle when starting Ubuntu"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by kazik1616 on 2014-03-05
Hi all,
My Ubuntu was working correctly for couple of months. But when I wanted to start it today, it hang. When starting in recovery mode the last message I see is following:

init: Failed to spawn friendly-recovery pre-start process: unable o getpwuid: Stale NFS file handle

What is amazing, I have never used NFS. Did I modify something accidentially?

How can I repair it from livecd? Which files to look into my drive?

I am using 13.10

[ATTACH=CONFIG]250877[/ATTACH]

---

### Post by kazik1616 on 2014-03-11
It seems that my / partition has been corrupted. I was not able to mount it from live cd. I have formatted it and reinstalled the system. That fixed the issue.

---

