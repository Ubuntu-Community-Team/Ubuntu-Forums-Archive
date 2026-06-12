---
title: "four window primary partition problem"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by alokmahor on 2013-04-16
Hi everyone,

I have to install Linux on one friends laptop without wasting time in backing up or moving data here and there.


 the hard disk scene is 


/dev/sda

   /dev/sda1  of about 100MB which is part of window 7 installation

   /dev/sda2 of about 300GB which contains window 7 OS, have lot of free space 

    /dev/sda3 of about 10GB which is recovery drive

   /dev/sda4 of about 100MB which is HP_TOOLS


I will use free space from sda2. but 4 primary partitions are already created so I cant create new partition. 


earlier I used to convince people to delete Recovery partition as they had C/DVD's of window and drivers


but  some people dont have CD/DVS's of window and drivers so I have to take  long time to decide what should I do in this case as I dont want to  waste my time in creating recovery DVD's for them.


do anyone have idea how much HP_TOOLS (sda4) is significant?  what if I delete this small partition? does this drive contains  something important for laptop?


or suggest me what should I do in such cases?


or can we convert primary partition to extended/logical partition?

---

### Post by oldfred on 2013-04-16
Some have said you can backup or copy to main Windows install and restore to a new logical partion and it still works. Supposedly you can also download from HP.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Still best to have full set of DVDs to restore system or maybe better a full backup.
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by alokmahor on 2013-04-16
thank you 
i will delete hp_tools partition then.

---

