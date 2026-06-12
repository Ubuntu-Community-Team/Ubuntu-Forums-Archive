---
title: "Buffer I/O error device hdc"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by dptxp on 2007-04-05
While I had no problem installing Ubuntu(64 bit, 6.10) in laptop and running 7.04 (64bit) live (I chose not to install), I am having problem in even running on desktop.

With 7.04 alpha, the Kernel loads about 3 to 5% only.
With 6.10 the Kernel loads but then I get following:

XXXXXXX (some no.) buffer i/o error device hdc  XXXXXXX (some number)
This i/o error keeps on coming up with different numbers.

THe desktop is 2500+ 64 bit Sempron, Via chipset, 256 MB RAM (64MB goes for
shared video). 80 GB SATA HDD, CDRW as Secondary Master. Mode SATA (not RAID)

I tried different booting options by adding
1) pci=acpi      (for via chipsets)
2) noapic nolapic

Nothing worked.

Somewhere I read that that the 80 core cable be replaced with a 40 core for CD Drive.
I do not have one, tried to get.

Can anyone help ?

---

### Post by genecaldwell on 2007-04-05
I'm having this very same problem right this very minute( came here looking for help so I stopped my install)  , and I have no clue what an 80 core or 40 core cable is, and I've been building my own computers for over 10 years now. it really looks like all the newer releases are having many more hardware problems than the releases that were being released as little as a year ago. So what I am saying is that If Hoary did not have this problem and ran just fine on my target computer, then how can it be a problem with my cable ? why would it be a problem with my hardware today when I had no hardware problems last year ? 

update , I just installed 5.10 no problem, no hardware problems at all. the above issue was trying to install 6.10

---

### Post by dptxp on 2007-04-06
Did you try Dapper Drake (6.04) ? At least it is latest LTS version. Reviews say that FreeSpire and SimplyMepis have much better hardware compatibility and they are now Ubuntu based. You can use DapperDrake repositories in SimplyMepis, have not checked FreeSpire.

There should be answers to such generic questions somewhere.

---

### Post by pixeldotz on 2007-04-10
i was browsing looking for this same issue. i'm having MAJOR problems installing 6.10 or FIESTY on my desktop. so i'm going to try dapper drake and then run the updates.
running the alt cd install kept saying my hdd had badsectors (which it doesnt after continous test and scanning) and those bad i/o device hdc stuff.

also, fyi, my laptop (which im on right now) is running 6.10 without a hitch.

cpu. 2.0
ram. 1024
hdd, 40, 80, 300, 300 (lots of music and video editing)

atleast im having fun trying to get this working :)

---

### Post by dptxp on 2007-04-11
I changed the CD drive. It was perhaps a bit bad.
Kernel loaded but got stuck up later.

FreeSpire 1.0.03 64 bit live CD runs, though quite a bit slow due to the RAM.
SimplyMepis 6.5 64 bit took eternity but loaded.

And both are Ubuntu based.

I guess that 80-wire cable is not the problem.
64 MB of the 256 MB RAM goes to shared video memory, 192 MB may be low.

FreeSpire and SimplyMepis ran (not ran really)  because unlike Ubuntu they have KDE.
In Ubuntu, Gnome was the problem, needs more RAM.

---

### Post by pixeldotz on 2007-04-11
so i was able to finally get ubuntu installed. it's running but i can't tell how well. i have to do 2-3 hard resets before it gets passed the hanged up OK BOOT KERNEL message.

installed 6.06 dapper.
upgraded via the instructions on the wiki to 6.10.
from 6.10 i upgraded via the wiki instructions to 7.04 beta to get ntfs support setup and just to be upgraded.

i really don't what else to do anymore either.

hope this info helps you.

fyi: all my cables are 80 wire ide cables.

---

