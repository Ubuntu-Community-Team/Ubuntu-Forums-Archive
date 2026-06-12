---
title: "Help with partitioning for dual boot with windows 10?"
date: 2016-03-26
forum: Installation &amp; Upgrades
---

### Post by foxj.1994 on 2016-03-26
Hey, so I'm trying to install Kubuntu alongside my win10 installation.

I don't have a CD drive so I've put it on a USB. My PC uses BIOS rather than UEFI so it worked fine. I shrunk my C:\ drive by 60gb in windows disk management, however, when I went to install on boot-up, the 60gb partition was listed as "unusable".
I looked online and apparently this could be because I've exceeded my max amount of partitions and so it's been made unusable.
I've looked online at solutions to this but I really don't feel comfortable understanding/doing what any of them suggest as I'm not the most knowledgeable on the subject and am afraid of messing something up. If anyone could give me a step-by step of how to resolve this for my system in particular (so I know I'm definitely doing the right thing, merging the right partitions etc.) it would be much appreciated :)

Here is a screenshot of windows disk management tool with all my current partitions:
[IMG]http://puu.sh/nUEpf/b260aec465.png[/IMG]

---

### Post by oldfred on 2016-03-26
Often you have two partitions you can backup & delete, both recovery partitions, so you need to make those recoveries first.
One is usually a vendor recovery, which can restore system to as purchased. Often really on useful if selling system. Some may kept your data, but better to do your own full backup first.
One is often a vendor tools partition. Those files often are small so easily backed up and many vendors let you download those again if needed.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

With my Windows 8 system, I made Dell recovery, Windows recovery and a full backup with Macrium. Multiple DVDs & a couple of flash drives, one was 8GB and the full backup used about 26GB on a 32GB flash drive. And I had not installed or added any of my own data.


 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by foxj.1994 on 2016-03-26
In this scenario can I get rid of the 136gb partition then? I really have no idea what that partition is. MY HDD should be 1TB, and it says it's free space. Is that a recovery partition that I can delete?

Extra info: My OS was windows 7, one that I bought myself, didn't come with the system; I then upgraded to windows 10.

[edit]
I just noticed that that partition doesn't show up in the top pane. I really have no idea what it is :S

[edit 2]
OK so that 136gb is apparently an extended partition. It won't let me delete the partition.

---

### Post by oldfred on 2016-03-26
Your 137GB is not a partition, it just is unallocated space.
And when you have used all 4 primary partitions, it has to remain as unallocated, unless you delete one primary.

Some have been able to use fixparts or Windows tools to convert a primary partition to a logical. Then they can expand the extended partition that the logical is in to include the 137GB (if next to it). You have to follow partition rules that all logical must be in one contiguous extended.
       [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by foxj.1994 on 2016-03-26
Okay I think I understand. Out of my partitions are there any that I can just get rid of in order for my 60gb one to be usable? There's C:\, System Reserved (100mb), Recovery Partition (449mb), and some random 4GB Primary Partition

[edit]
Alternatively, is there any way for me to move the Free Space next to my C:\ drive so it will let me delete it and change it to unallocated?

---

### Post by oldfred on 2016-03-26
See post #2
Most delete vendor tools. But you can backup & restore to a logical partition, also.

---

### Post by foxj.1994 on 2016-03-26
Thanks for all the help :)
It's all sorted now, I deleted the 4gb partition (which I can only assume was a swap partition), so it merged with the free space, then deleted the recovery partition and merged the two free spaces together, put ubuntu on that and created another 5gb swap partition.

I've gotta reinstall it because I managed to mess everything up through installing an AMD proprietary driver and shutting down my PC mid-process when it crashed (kek), but that's another story :')

---

