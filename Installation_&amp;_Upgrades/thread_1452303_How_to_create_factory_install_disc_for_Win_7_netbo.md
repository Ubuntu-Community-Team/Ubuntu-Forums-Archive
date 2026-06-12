---
title: "How to create factory install disc for Win 7 netbook in case Ubunu borks?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by CTenorman on 2010-04-11
Hi,

I've just gotten a gateway netbook I'd love to throw a copy of ubuntu on. However, before I install I'd like to create a backup factory install disc. The problem is I don't have a DVD drive in my netbook.

Is there a DVD writer program for Windows or something similar that would simulate the presence of a DVD drive and allow a backup DVD to be written to it? Does anyone have any other suggestions?

Thanks!

---

### Post by wilee-nilee on 2010-04-11
I would call the computer manufacturer and get a DVD for re-installation or a ISO. The ISO can be loaded onto a thumb with MS usb loader. In the end having a full installation disc is a goos thing to have.

Windows has it's own backup system that can be done with a external device like a hard drive, I don't use it so I can't really help you there. 

There is a windows 7 forum that might have the info you need for backing up if none is found here.
This is a pretty busy forum not as many members as this one but useful nonetheless. 
[http://www.sevenforums.com/](http://www.sevenforums.com/)

So if you decide to do a dual boot make sure you use the disk management virtual partitioner in W7 to adjust it's partition size. If you can if your unsure about any of this post and somebody will help if needed.

There are several options to running Ubuntu, it can be fully installed onto a large enough thumb, or the ISO mounted on a thumb that boots and saves updates. These two methods are done with no changes to your computer.

You could also install the sun Vbox in W7 and run it from there, I like this better then a wubi install myself.

Also your computer must already have a recovery on it which is basically, or should be the gateway install minus the disc. Disk management shows you the partitions so look for that.

---

### Post by CTenorman on 2010-04-11
I'm going to answer my own question here in case anyone else has the same issue.

I found a program called Virtual CD, [http://www.virtualcd-online.com/](http://www.virtualcd-online.com/) . Essentially it lets you simulate any kind of drive you want and burns the ISO to your hard drive, where you can copy it to a USB stick and burn the image on another computer.

With that done, you can mess up your main partitions with abandon - just be sure that the disc images really are verified!

---

