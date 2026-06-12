---
title: "Grub rescue, boot repair didn't work?"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by t_20 on 2012-06-27
Hi I'm a newbie, so in dire need of help.

I had Windows7 and Ubuntu 11.10 on dual boot, was working away on Ubuntu when it crashed and the the following appeared

Partition not found
Grub Rescue>

I tried booting using hte root, chainloader method but it wouldn't recognise the chainloader command.

I created a boot repair disk and ran the recommended repair option, but that didn't work. Here's the summary:

[http://paste.ubuntu.com/1062599/](http://paste.ubuntu.com/1062599/)

I tried running the same boot repair disk again, to do an advanced repair, but it won't load - it seems to be stuck a get a continous line of errors. 

Could you please have a look and let me know that I haven't screwed up completely? 

Thanks in advance

---

### Post by oldfred on 2012-06-27
Welcome to the forums.

This does not look good as Boot_repair did not see anything at all.
> Invalid MBR Signature found.

It is not showing any partition table at all.

From liveCD and Disk Utility what does it say about hard drive under Smart Data. It has lots of detail, but all I know is green is good.

If drive is ok, then I would try testdisk. That may be able to recover partition table.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by t_20 on 2012-06-27
Thank you for your reply oldfred - it seems my hard disk has died ;(  
Dell should replace it though.

---

