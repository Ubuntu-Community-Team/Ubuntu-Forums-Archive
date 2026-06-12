---
title: "Make Installation Easier for Windows user"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by tripleboot on 2007-05-03
Holy smokes Ubuntu, this is ridiculous.   I'm dual booting Vista and XP right now and I've also had SuSE 10.2 installed which was a real simple automatic process I could understand.  I've partitianed my hard drive using Acronis Disk Director Suite and created a seperate 10gb partition for Ubunutu (Fat32) and also created a 1gb swap partition.  When I go to boot up the Ubuntu 7.04 and get to the desktop and then go to install and the nightmare starts.  WTF is all the giberish.  Can't you give me a list of partitions on my HD to choose how to install..  I have no clue your manual language and don't care to spend allot of time trying to figure this out...  If you want to get more people to convert from windows then you need to make this install process more simplier to understand the way SuSE 10.2 does...  Thanks.

---

### Post by AdHavoc on 2007-05-03
Well, I'm pretty sure Ubuntu can't run on a FAT32 file system, but the installer will automatically format it to ext3 so there's no problem there.  As for partitioning, the partition manager may seem intimidating at first, but it's fairly straightforward.  You first choose a hard drive to install Ubuntu on, then choose a partition on the hard drive.  In your case, you would choose the 10 GB one you set aside for Ubuntu.  Then install Ubuntu on it and you should be good to go.  And as for languages, Ubuntu prides itself in being a fully international organization; I'm sure your first language is supported.

---

### Post by tommcd on 2007-05-04
As in the above post, you can't install linux to fat32 partition. Linux can read and write to fat32 data partitions though.
When you get to the partitioning part, choose the 10GB partition to install ubuntu to. Choose to format it, and choose ext3 file system type. Also, choose / (root) as the mount point. If you have a seperate /home for Suse you can share that with ubuntu. Don't choose to format the partitions you want to keep. If you notice, when you get to the partitioning part, Suse will probably be identified as ext3 (or possibly reiserfs or xfs) file system type.

---

### Post by aysiu on 2007-05-04
I'm sorry but what's  the point of this thread? If SuSE works for you, use SuSE. Ubuntu does things a different way, and other people seem to like Ubuntu. Use what works for you.

And if you have more specific criticisms than "WTF" and "gibberish," file a bug report or write a spec for the upcoming Ubuntu release.

The way the thread is constructed now, I see no point in this continuing.

If you want help, ask for it. If you feel there's something wrong with the Ubuntu installer, file a bug report:
[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntu](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=&search=Search+Bug+Reports&field.scope=project&field.scope.target=ubuntu)

---

