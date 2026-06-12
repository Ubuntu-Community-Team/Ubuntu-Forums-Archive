---
title: "Sorting Partitions to Install Ubuntu 13.10"
date: 2013-10-28
forum: Installation &amp; Upgrades
---

### Post by NoFriends on 2013-10-28
Alright guys,

Below is a screenshot of my current setup, it was like this when i purchased my HP Pavillion G 6 Laptop.

Now, all i want to do is install ubuntu without causing my current windows 7 to have any issues, but it's appearing to be a pain in the backside.
I've been told i have to increase the size of Recovery on D Drive & Copy HP Tools on E Drive onto D Drive, but i don't want to cause any errors etc 
when trying to load windows or Ubuntu.

Someone on here did mention i a only able to have 4 partitions and no more, it's a shame HP have made this really difficult, feel like giving up attempting.
[IMG]http://s9.postimg.org/70zl22ifz/Layout.png[/IMG]

If someone can explain in detail for someone who has't used ubuntu in many years, that would be great.

---

### Post by oldfred on 2013-10-28
HP and almost all Windows 7 systems use all 4 primary partitions. Most seem to have best sucess with backing up & deleteing the hp tools partitions. Those files supposedly are also available to download.
But you really should make a set of recovery DVDs and then recovery partitions has less value. And a set of DVDs that is a full backup as you may have modified systems a lot and recovery just restores to as purchased.
Also make a Windows repairCD.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

