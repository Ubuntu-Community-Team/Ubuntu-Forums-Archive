---
title: "Odd Install Configuration - Can It Be Done"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by bugwump on 2008-06-18
Hello Ubuntu Community!  

I have dabbled in Linux for fun in the past, used to have a RedHat webserver(family photo album with accounts for all my family to log in and upload albums, etc)/fileserver/print server/ftp server.

I am also an experienced Unix Systems Manager so I am familiar with the Unix CLI and internals, but not so much with the differences within Linux.

At any rate I have kind of a strange situation, and am interested in whether or not this can be pulled off easily.  I have a laptop with a 250gb drive.  It has three partitions.  One for Windows XP, one for Windows Vista and one for a common data/programs volume.  I returned my laptop (unhappy with it) and my buddy borrowed my drive for his new laptop while waiting for his new hard drives to come in.  He installed HIS Vista64 on the vista partition and left my XP and data partitions alone.

I have my new laptop and my drive back.  My XP partition is still there and I'd prefer it remain in tact.  My data partition I'd like to preserve as well.  The vista partition is no good to me, it isn't even an active copy anymore. I'd like to be ubuntu on that partition while preserving everything else.  Is this possible?

Is it also possible to use the common data area as a shared area for both ubuntu and XP?

Any help would be appreciated.  I am looking to load this on a Sager 9262 with a Q9450 2.66Ghz Quad Core processor, 4gb of memory and SLi Nvidia cards on it.  I already tracked down the latest nvidia drivers for the cards, so that is good.

Thanks for all your help!!

---

### Post by Sef on 2008-06-18
> I have my new laptop and my drive back. My XP partition is still there and I'd prefer it remain in tact. My data partition I'd like to preserve as well. The vista partition is no good to me, it isn't even an active copy anymore. I'd like to be ubuntu on that partition while preserving everything else. Is this possible?

Yes, it is.  You can reformat that partition and everything else should be left alone.  You will need to set up a swap partition also.  

For more information, read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").  

1) **Back up** your data first.  As you well know, there are no 100% guarantees.

2) To read and write to your home paritition, which is most likely NTFS, download NTFS-3 from the repositories after installing.

3) Ask more questions if anything happens.

---

