---
title: "Cannot Detect Hard Drive"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by mr.moch on 2012-12-10
I am trying to install Ubuntu 12.10 via USB on my Dell Inspiron 910 netbook.  When reaching the list of disks to install Ubuntu on comes up, the list comes up completely empty.  Is there something I'm missing?

---

### Post by oldfred on 2012-12-11
Do you have Windows 7? That almost always uses all 4 primary MBR(msdos) partitions.

Post this from terminal or screen shot from gparted.

sudo fdisk -lu

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

    
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

