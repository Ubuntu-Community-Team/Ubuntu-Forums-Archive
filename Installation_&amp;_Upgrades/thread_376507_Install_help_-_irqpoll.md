---
title: "Install help - irqpoll?"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by aggierandy on 2007-03-05
I was attempting to install Ubuntu 6.10 on an old custom built Pentium III computer. I was having trouble and consulted these forums. My computer would freeze upon loading root file system and then say Alert! Buffer I/O error on device hda1, logical block 'X'. The X would either be a 0,1,2, or 3. I followed the instructions and hit F6 while loading and it took me to a command prompt where I type irqpoll. The system then loaded and took me to the desktop. I thought all was well and double clicked the install folder and began. I got to the "select Time zone" screen and it automatically took me to a login screen. It said "username ubuntu will auto login in XX seconds." and it counted down from 30. When it logged in I attempted to install again and it immediately took me to this login again. I tried once again and the desktop would not load. I have a cream colored screen and a mouse that moves but nothing else. What should I do. I know that the irqpoll problem seems to be common but I was hoping I got past it.

My system is a Pentium III 550MHz with 256 ram and a single 40 gig hd, a floppy drive and a Cd-RW drive. Other than that I don't know what to say. Any advice guys.

P.S. I am pretty new to ubuntu and so far I have had very limited success with installation. I was hoping to revitalize some old PC like I had heard stories of but so far I keep coming up short! Thanks in advance for all of your help and understanding.

-Newbie

---

### Post by aggierandy on 2007-03-05
well I tried adding this boot option:


irqpoll pci=noacpi noapic nolapic acpi=off

to no avail seems to be caught in the same loop. Ill keep diggin through these forums and try to get something positive.

Also it is saying "I've detected a panel already running and will now exit." When I make it to the desktop for a few seconds. If I leave this up there I can keep it logged in. My CD drive keeps spinning up intermittenly though.

---

