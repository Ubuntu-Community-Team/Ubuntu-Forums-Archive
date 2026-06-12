---
title: "Problem partitioning for Kubuntu"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by steevc on 2006-06-04
I've been running Breezy on my PC, but I'm taking the opportunity to re-partition my drive when I move to Dapper as I managed to install Breezy with one big partition.

I have a 250GB drive and was thinking of:

20GB  for system
30GM for home
The rest for a bit of boot, some swap and my big data partition.

I'm trying to set this up in the installer, but it keeps telling me that it can't proceed because something is mounted. I can get to the bit where you tell it where things should go, but it just offers my existing boot and root partitions.

I've tried all sorts of combinations on this with no progress, so will give up for tonight. Suggestions welcome.

UPDATE: As I sort of expected I found that I cannot boot my old system any more as the partition has been overwritten. Also, I have no plans to dual boot any form of Windows.

---

### Post by steevc on 2006-06-06
In case anyone else has the same problem, I resolved this by partitioning as shown at 

[http://www.psychocats.net/ubuntu/windowstoubuntu.html]("http://www.psychocats.net/ubuntu/windowstoubuntu.html")

I created an extended partition with the various partitions I wanted in it. All working and I'm happy :)

The actual Kubuntu install was very quick.Now I need to install all the extra stuff I use.

---

