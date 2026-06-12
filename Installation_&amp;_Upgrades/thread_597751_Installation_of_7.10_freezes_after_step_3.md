---
title: "Installation of 7.10 freezes after step 3"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Sp1kez on 2007-10-30
I boot the cd and everything works fine, I go into the live CD and run "install" I get past the choose language, zone and keyboard and when I click forward it begins searching for partition and when the bar gets full the window goes away and im stuck at thenstep 3 of 7 screen


I have already burned two other cds just to make sure and same problem.


(I thought after selecting keyboard layout u were asked username etc instead of partitioning stuff?)


Last night I left it on after I clicked forward on step 3 and this morning it was on the "select partition" window but there was nothing listed, I went to places> computer and my hdd wasnt listed, it is listed when i start up the live cd though...


anyone else getting froze after selecting keyboard layout?

---

### Post by Jeff12088 on 2007-11-04
Same problem here as well.

After selectin the keyboard layout, the loading screen for the partition manager shows but then nothing happens. Just stuck at the third step.

---

### Post by Orius on 2007-11-05
Having a similar issue while attempting to install to an external USB Hard drive.  The partition manager run via the LiveCD has crashed several times prior to running the install, perhaps this has something to do with it?

---

### Post by Hans Bijen on 2007-11-05
I tried to install on a raid 0 disk. This failed because Ubuntu installation
didn't recognize the raid 0 disk. So I tried to install on a USB external drive. This also failed, because Ubvuntu could not create the swap partition on the external USB-drive.

Hans Bijen

---

### Post by phrostbyte on 2007-11-05
This may be because you have a lot of partitions or a partition which is confusing the installer. This is probably a bug, if you please can fill a bug report on [http://www.launchpad.net/](http://www.launchpad.net/) with your HDD configuration and hardware it would be helpful.

---

### Post by Sp1kez on 2007-11-13
I still havent been able to install, it just gets stuck there......


I tried on a different pc and it gets to the part where I select how to partition, then after I select it goes to partition and stays there.......


Do you have to partition the drive you want it installed on with the windows boot cd before you start install of Ubuntu or do you need to have it formated as NTFS or FAT32? or not formatted at all? what is the deal?

---

### Post by SpiritIsReality on 2007-11-13
howdy
You could use the gparted live cd, instructions at their site. Or you could try the alternate install cd. I use the both of them, and also  knoppix . They're great tools to add to the livecd of Ubuntu for just these reasons. Wireless problems too. I
Networking, I'm just learning about it. It's fun once you get past the gate.
Well unless you enjoy locked gates. haha!
[http://www.google.ca/search?hl=en&q=gparted+live+cd&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=gparted+live+cd&btnG=Google+Search&meta=)
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://www.google.ca/search?hl=en&q=knoppix&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=knoppix&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+alternate+install+cd+7.10&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntu.com+alternate+install+cd+7.10&btnG=Google+Search&meta=)
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)
trails

---

### Post by Sp1kez on 2007-11-13
I was able to install on the second PC, however on the first one I still have that problem as when i started this thread.

What is going on there? it just gets stuck after step 3 and after the paritioner window comes up....it never takes me to the part where I select partitions...


Does the hard drive need to be partitioned or formated before I try to install? Should I format it NTFS or FAT32?

---

### Post by AllWires on 2008-04-09
I'm having the exactly same problem. I have two hard drives. A 120GB Maxtor with junk on it that I don't need (that is the hard drive I will install Ubuntu on), and a 200GB Seagate Barracuda with my windows XP stuff which I am not touching.

(The installation worked fine from my laptop installing onto a pendrive)

---

