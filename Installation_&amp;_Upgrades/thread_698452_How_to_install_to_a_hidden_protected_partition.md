---
title: "How to install to a hidden protected partition?"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by bbgobie on 2008-02-16
I wish to install Ubuntu to a protected restore partition much like the eee PC and other preconfigured OEM systems do.

In that way it's always easy to restore back to the original install.  How would I go about doing that? A quick search didn't turn up what I was looking for.

---

### Post by kidders on 2008-02-17
Hi there,

I suppose you could tarball a fresh installation, create a partition just big enough to fit it, and move it there for safe keeping. If you know what you're doing, you could safely archive a live OS that way, but otherwise I would suggest booting off a CD to do it.

That way, restoring a basic Ubuntu install would be a matter of "tar xjf"-ing it into a blank filesystem ... (bzip2 would probably give you the best compression). You'd also have the option of only restoring parts of it, if for example you screwed something up and needed the original configuration back, or something.

---

### Post by bbgobie on 2008-02-26
Thx,
Yes I think that should work.

Do you know how manufacturers do it? Like during boot, press F__, and the restore is done?

---

### Post by louieb on 2008-02-26
> **bbgobie said:**
> Do you know how manufacturers do it?...
Basically hidden partitions are built into the BIOS. Not something for the average user. Heres a blurb on how IBM does it. 
[http://www.thinkwiki.org/wiki/Hidden_Protected_Area](http://www.thinkwiki.org/wiki/Hidden_Protected_Area)

---

