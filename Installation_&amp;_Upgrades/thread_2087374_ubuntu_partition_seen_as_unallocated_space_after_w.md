---
title: "ubuntu partition seen as unallocated space after windows 8 upgrade"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by rooserik on 2012-11-23
Hello,
I use ubuntu 12.04 as my main OS, but I have a dual-boot with windows, for the rare occasions I need it for school. Today I decided to upgrade windows xp to windows 8 on the other partition. I read on some forums I would most likely need a live-cd to repair grub after upgrading windows, so I could boot into ubuntu again. After installing windows, I used the live-cd and the program "boot-repair". 

This is the url: [http://paste.ubuntu.com/1379830/](http://paste.ubuntu.com/1379830/)

However I still cannot get access to ubuntu and furthermore, according to gparted, the partition with ubuntu 12.04 is seen as unallocated space (!). Did I do something wrong, did I somehow remove ubuntu? Since I use it as my main OS, I really like to regain access to ubuntu, without having to reinstall it. Could someone look at my url of boot-repair, and give me suggestions what I could do?

Ps: I also added a screenshot of what I see on Gparted, when I use it from a live-cd

---

### Post by oldfred on 2012-11-23
With partition missing, Boot-Repair cannot find anything to fix.

Gparted has a quick repair, and testdisk can often find all the old partitions on drive.

       GParted's partition-recovery tool.
Device -> Attempt Data Rescue in GParted

    
if that does not work.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
            Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

