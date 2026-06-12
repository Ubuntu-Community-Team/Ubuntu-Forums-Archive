---
title: "Switching from WUBI to partition"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by svc1 on 2012-01-03
Hi,

 I think I am at the limit of my wubi (16GB). I decide to make a new partition and get rid of the size constraints of wubi.
   
  Is there an easy way to migrate from wubi to a partition? In other words, let’s say I make a new partition on my hard disk. Is there a way of transferring my wubi installation onto the newly partitioned space?
  
Thanks,
S

PS: I am using Ubuntu 10.10

---

### Post by Frogs Hair on 2012-01-03
A Wubi installation can be moved to a partition but it is a bit of work   . It may be easier to remove Wubi and install a traditional dual boot .

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (Wubi Mega)   

[http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition](http://ubuntuforums.org/showthread.php?t=1519354&highlight=wubi+partition)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by svc1 on 2012-01-03
Sorry, I wasn't clear.


What I am trying to do is to create a dual boot.

Once a dual boot created, is there a way to transfer the wubi installation to the new boot and destroy the wubi afterwards?
   
Thanks,
S.

---

### Post by fantab on 2012-01-04
> **svc1 said:**
> Once a dual boot created, is there a way to transfer the wubi installation to the new boot and destroy the wubi afterwards?

No, I don't think there is safe method to transfer Wubi to the new boot.

What you can do is BACK UP your DATA that you may have in Wubi and remove wubi. Then go on to install Ubuntu to a partition. Then off course you can reclaim your data from BACK UP.

---

### Post by bcbc on 2012-01-04
You can migrate a wubi install using the script here...
[HOWTO: migrate wubi install to partition]("http://ubuntuforums.org/showthread.php?t=1519354"), as mentioned by Frogs Hair.

1. Create partitions
2. Download script
3. Run script
4. Remove Wubi 

That's about it. Any questions feel free to post on that thread.

---

