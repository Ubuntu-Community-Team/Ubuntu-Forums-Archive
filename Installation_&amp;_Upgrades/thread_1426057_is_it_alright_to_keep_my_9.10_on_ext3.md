---
title: "is it alright to keep my 9.10 on ext3?"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by superarthur on 2010-03-09
When I searched on the internet on how to install ubuntu, I came across a page that told me to use Partition Manager to create a ext3 partition first. As a result, I installed Karmic on ext3.
Then I saw that Karmic is installed on ext4 by default. Is there going to be a problem if I keep running Karmic on ext3, or do I need to upgrade to ext4? If it's better to upgrade, how do I do it safely?

---

### Post by efflandt on 2010-03-09
ext3 is more mature and is what I am using.  ext4 is slightly faster, but is newer, so older tools or Linux versions may not be able to access it.  There is more of a chance that data might be lost due to its delayed allocation if your system tends to lock up or power off unexpectedly.  But newer kernels and Ubuntu have taken steps to minimize that issue.

I have never knowingly lost any data during lockup or power failure of any system using ext3.  But I use an uninterruptible power supply and try not to do things that would lock up or hang my system.

There is no pressing need to change.  It is just another option if you want to try it.

Some info about ext4 [http://en.wikipedia.org/wiki/Ext4](http://en.wikipedia.org/wiki/Ext4)

---

### Post by sxmaxchine on 2010-03-09
i dont think there will be any major issues just a slight speed difference, there is also the problem of ext3 not being able to support bigger hard drives then ext4 (not positive that true i just read it a while back)

---

