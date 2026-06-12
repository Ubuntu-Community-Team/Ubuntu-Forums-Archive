---
title: "Ubuntu 13.04 Installation: Partition sizes different from Windows 7"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by prasunvelayudhan on 2013-04-26
I'm trying to install Ubuntu 13.04 in my system. 
Windows 7 already installed in my system, so using windows partition manager i created a 20 GB partition just for Ubuntu.
But when i try to manually select the partition during Ubuntu installation The sizes mentioned are completely different.
Please check the screenshots below.
Please advice how can i select the 20GB partition created for the installation.
[ATTACH=CONFIG]241814[/ATTACH][ATTACH=CONFIG]241815[/ATTACH]

Thanks

---

### Post by fantab on 2013-04-26
You were only supposed to have 4 Primary partitions. By forcing the Fifth Windows changed the "BASIC" partition type to "DYNAMIC". Linux will neither recognize nor install to Dynamic partitions. Dynamic Partitions are Windows proprietory. 

You should First BACK UP all your important DATA to safe place. Then: 

DELETE all partitions, Recreate them and re-install everything.

OR

Read [**HERE**]("http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html").

---

### Post by prasunvelayudhan on 2013-04-26
Hm.. If i delete that 20GB partition in windows and made it unallocated space. Will it be recognized by Ubuntu?

---

### Post by fantab on 2013-04-26
NO. Not until the Dynamic 'Disk' is converted back to 'Basic'. The HDD has turned to 'Dynamic' not just the partition.

---

### Post by prasunvelayudhan on 2013-04-26
:( that's gonna be pain... 
Anyways... thanks for your time and advice :)

---

### Post by fantab on 2013-04-26
Well that's exactly how 'closed source' proprietory-ware is. 

You are welcome. And Good Luck...

---

