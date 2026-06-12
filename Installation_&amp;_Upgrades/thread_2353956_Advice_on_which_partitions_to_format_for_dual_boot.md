---
title: "Advice on which partitions to format for dual booting Windows 10 and Ubuntu?"
date: 2017-02-26
forum: Installation &amp; Upgrades
---

### Post by andreign on 2017-02-26
I have this lenovo laptop (l440) which currently has windows 10 installed (had windows 7). I want to dual boot with ubuntu however it already has 4 partitions on it. From what I understand the 4th partition can be formatted but what about the first 3? I already made recovery disks for Windows.  i don't want to to get rid of my Windows system or files. I want to get the option "Install Ubuntu alongside Windows" during installation

What partitions are OK to format to make space for Ubuntu? It need 2 free partition spaces for installation right?

Below are my GParted and Windows disk management screenshots:

[IMG]http://i.imgur.com/9KnenTH.png[/IMG][IMG]http://i.imgur.com/KmD80qD.png[/IMG]

---

### Post by oldfred on 2017-02-26
Is sda3 more like other vendor's system tools partition. Its not large, easily backed up & then gives another primary partition to convert to the extended and have many logical partitions. You still will have to shrink sda2 to make room. Use Windows to shrink sda2 and reboot immediately so it can run chkdsk and update to new size.

       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

