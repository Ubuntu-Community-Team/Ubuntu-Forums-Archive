---
title: "Ubuntu Installer freezes after Keyboard layout"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by ijusten on 2008-03-21
Hi!
After succesfully upgrading my laptop to Ubuntu from WinXP, I decided to bite the bullet and try to install Ubuntu on my desktop.

I first tried to use the Wubi 8.04 Beta, and it worked splendidly with the start-install-in-Windows, but after booting in Linux and asking would I want to bring my settings from Windows over, it freezes; the "NEXT"-button stays gray.

After hitting Cancel and thus getting to the regular old LiveCD-stage, I try to Installation the old-fashioned way. Everything goes as normal till I try to move to Step 4 (Partition Manager). It waits a long time untill it gives error titled "??? ???", The same text doubles for explanation. I push forward and it only shows one possible partition (I have three hard drives split to about seven partitions). 
I note I can't access these partitions from "Computer" either.


I try the above with the Wubi 7.04 Installer. I never get to the desktop; it starts asking something weird in the DOS-like stage (I'm sure there's a proper name for this) and I cancel.

I try to install Ubuntu again with 7.10, I burn the CD and everything. Everything goes as described in the Beta-thingy. The only difference is that this time I can access the partitions physically and the partition manager never pops up; instead I'm stuck in the Keyboard layout and the six questionmarks pop up again and again.


I don't really know what I should tell about my computer configuration. Any hints would be apreciated.

---

### Post by Pumalite on 2008-03-21
Processor, memory, graphics to start with.

---

### Post by ijusten on 2008-03-21
> **Pumalite said:**
> Processor, memory, graphics to start with.

Oh yeah. I have AMD64 processor. I'm not altogether sure on it's brand name, but it was supposed to be "3000+".
1024 RAM
GeForce 7600 GS.

---

### Post by Pumalite on 2008-03-21
You should have no trouble. I'd go with a 64 bit. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
The Alternate is easier to install.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x, on CD-R, check CD integrity after burn and before install.

---

### Post by ijusten on 2008-03-21
> **Pumalite said:**
> You should have no trouble. I'd go with a 64 bit. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
The Alternate is easier to install.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x, on CD-R, check CD integrity after burn and before install.

I have livesession going on burned Ubuntu 7.10. It passes integrity test. I don't think that's tthe problem.

---

