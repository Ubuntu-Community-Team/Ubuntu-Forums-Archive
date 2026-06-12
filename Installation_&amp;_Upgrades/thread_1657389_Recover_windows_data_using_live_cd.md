---
title: "Recover windows data using live cd"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by nipunreddevil on 2011-01-01
I recently tried to partition my hard disk so that i could use a separate drive for installing ubuntu.However after the partition manager took a reboot,i'm not able to boot into windows.Moreover when i tried to use Ubuntu live cd,it doesn't show the newly created drive.I also wish to retain all my windows data which is quiet critical.However when i tried to mount,i got the following error which is attached as a screenshot.How can i 
1.Recover my windows data
2.Then be able to partition keeping windows intact
My laptop is Toshiba l305d-s5934

---

### Post by lithopsian on 2011-01-01
Run gparted and see what it says about the NTFS partition.  To be really safe, run it from the Live CD although that shouldn't matter until you want to change something.

---

### Post by oldfred on 2011-01-01
From a windows repair Cd I would run chkdsk. And rerun until there are no errors.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

