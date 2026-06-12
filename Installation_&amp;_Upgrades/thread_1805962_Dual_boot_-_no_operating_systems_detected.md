---
title: "Dual boot - no operating systems detected"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by ikzo on 2011-07-16
I'm trying to dual boot Ubuntu and Win7, and I just did a clean install of Win7.  However, when I start the Ubuntu installation it merely just says no operating systems detected and my only option is to erase the whole disk.  I can see the NTFS partition in disk utility but can't see anything in GParted.

I've tried to look through the forums but can't seem to find a solution to this exact problem - does anyone point me in the right direction or to the solution?

---

### Post by raja.genupula on 2011-07-16
you can install ubuntu with WUBI (install inside windows ). it will not erase your win 7. you can give what ever the size you want for ubuntu parttion . its safe to use .

---

### Post by oldfred on 2011-07-17
Most windows systems come with all 4 primary partitions used. They only think windows.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

