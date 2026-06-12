---
title: "Help pls - partition problems"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Florian Krenn on 2006-12-14
Hello,

I think I did a "great" job...
1) my machine was always dual boot, ABIT DigiDice, SATA HD - XP and RH Fedora Core 4; I wanted to install Ubuntu 6.10 from the live disk ... 

2) during install, I changed sda2 and sda3 space and it should have reformatted... sda1 is win

3) it stopped, I shut down and restarted; I restarted and tried the partition editor - no success; next try - it froze - I had to switch off

4) current state: Ubuntu does not recognize HD, I tried to get it fixed by trying to install minimum RH Fed. C4 with my old cds - also problem with partition sda3 !
I can manually boot windows with GRUB (that is being lucky)

Is there a way to get the linux partitions fixed ?
The machine boots, the "untouched" partition still works - so how can I fix that mess ....

Thx a lot in advance !

PS: I want to have a nice linux box ...

---

### Post by Sef on 2006-12-14
Try [GParted]("http://gparted.sourceforge.net/livecd.php") , [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12"), or [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by Florian Krenn on 2006-12-15
Thanks a lot for the links.

Anyway, I had also troubles with the partitioning tools. They simply did not recognize my disk. :( 

I then deleted the obviously damaged partitions with the WinXP harddisk manager (this program is so dumb that it even does not try to recognize any other type of FS) - this did the trick ! I could use the partioning tool, set up and format the partitions and voilà -
since yesterday member of the Ubuntu community ! :D

---

