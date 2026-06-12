---
title: "First Time Wubi Boot: Stuck at “Try (hd0,1) : NTFS5: _”"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by ronrr on 2012-07-15
Just installed Ubuntu 12.04 into Windows 7 via Wubi.

(Dell Latitude with an i3 CPU. This is my work laptop, so I don't know the full specs.)

Upon restart after the installation, it went to a screen that says:

> Try (hd0,1) : NTFS5: No wubildr
Try (hd0,1) : NTFS5: _

It's been stuck on that second line with a blinking cursor for ~60 min (since 8:30PM Pacific), almost like it's waiting for a prompt/command. Perhaps it's doing something, but my hard drive seems to be idle.

I've been reading through support docs & threads, and while I can find plenty of people with *similar* boot errors, I can't find any that exactly match my problem--specifically, hung up at the blinking cursor.

Any advice/thoughts/next steps? I'm hoping to avoid a hard restart for as long as is reasonable.

Normally I would partition my drive and go full install. This was just intended to be for evaluation purposes.

Thanks.

---

### Post by bcbc on 2012-07-15
Some people have solved this by copying wubildr to the first partition. I'd guess that there's something about the second ntfs partition that wubildr.mbr (grub4dos) cannot read it properly. But what that might be, no idea.

Definitely give up waiting if it's been 60 minutes.

---

