---
title: "Accidentally formatted /home partition - recovery?"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by sultanoswing on 2011-02-11
I was installing 10.10 x64 today. I wanted to manually partition the disks, since I have a /home partition from a 9.10 installation which I want to keep.

Unfortunately, I selected to convert the ext3 /home partition to ext4 and didn't realise it was formatting the partition until it had just begun. In desperation, I pulled the power plug, but now I can't access the partition (using the LiveCD) - comes with an input/output error.

What are some strategies to recover the data on the partly formatted partition? I don't think much, if any, was actually formatted.

Thanks in advance.

---

### Post by BACbOK on 2011-02-11
You can use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

---

### Post by sultanoswing on 2011-02-11
> **BACbOK said:**
> You can use [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk")

Thanks a lot. While waiting, I came across this thread: [http://www.0x61.com/forum/viewtopic.php?f=83&t=1157558&view=next](http://www.0x61.com/forum/viewtopic.php?f=83&t=1157558&view=next)

which also recommends SystemRescueCD, which prominently features testdisk amongst other recovery utilities. Fingers crossed!

---

### Post by sikander3786 on 2011-02-11
Or if you are unable to recover whole of your partitions, you can try recovering your files using photorec.

[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by sultanoswing on 2011-02-12
SystemRescue's suite of partition recovery utilities couldn't recover the bad, partly formatted partition (or to be more precise, I couldn't get it done with those tools).

Next up, photorec did recover lots of files - but more of them much older than the recently formatted ones. 

Oh well - live and learn (to backup). Careless mistake really - although perhaps a little more warning or leeway in the installer when it comes to formatting and partitioning would be helpful for idiots such as myself.

---

