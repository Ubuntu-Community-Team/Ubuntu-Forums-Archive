---
title: "Problem - Can't install Ubuntu 12.04.2 on laptop"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by barrybear on 2013-07-08
Hello all, I'm using a Sony Vaio T11113 laptop which has preinstalled Windows 7 Home Premium x64 bit. I'm not sure about whether it has RAID and all that as I only see two options in BIOS > Advanced that are Intel Virtualization Technology and Intel Safety.

I'm planning to do a dual boot, but whenever installing Ubuntu through a USB drive, after stating I do not want to connect to the WiFi, it automatically jumps to choosing harddisk for installation. But there's only a blank space with no information whatsoever about the hard disk.

---

### Post by dino99 on 2013-07-08
you can choose the manual install (aka "something else" option)  [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by barrybear on 2013-07-08
> **dino99 said:**
> you can choose the manual install (aka "something else" option)  [http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

Will it be okay to have another 3 partitions? There's already two/three partitions for Windows..

---

### Post by barrybear on 2013-07-09
I've tried the link above to manually create my own partition but it is not working! :( there's still no partition being shown at the installation page

---

### Post by oldfred on 2013-07-09
Most Windows 7 systems use all four primary partitions. You have to convert one primary partition to an extended partition which then is a container for as many logical partitions as you want.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.

While on HP, it really is the same for all Windows 7 systems.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

