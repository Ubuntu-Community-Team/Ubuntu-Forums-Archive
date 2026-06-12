---
title: "Just Upgraded to 7.10 and can't seem to find my partitions"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by Malissin on 2007-12-12
Alright, to quickly recap my box is an Compaq Presario AMD64 and is dual-booting Windows XP.  Previously under Ubuntu 7.04 that was all just working fine.  I recently upgraded to 7.10 using the Update Manager and everything appeared to go just fine.  Right up until I realized I could no longer view my Windows files while logged into Linux.  

The files are still there, booting into Windows still works fine, really I've just lost the convenience of being able to look at both sets of files from Ubuntu...but it was a really convenient convenience and I'd like it back.  Did 7.10 somehow lose the ability to view NTFS?  Did I screw something up during the install that I was unaware of?  Any help/suggestions appreciated.

Thanks, in advance
          Joe

---

### Post by louieb on 2007-12-12
Hello Joe,   Gutsy has read/write NTFS support. This machine is Linux only. Have to look at my laptop - it dual boots - when I upgraded it to Gutsy the XP partition change from read only to read/write.  

Might want to look at the psychocats link. There is a page on mounting windows.

Good luck.

---

### Post by MeathooK427 on 2007-12-12
Double check that the partition is mounted and ntfs-3g is installed (it should be by default in gutsy).

---

### Post by Pumalite on 2007-12-12
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

---

### Post by Pumalite on 2007-12-12
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

