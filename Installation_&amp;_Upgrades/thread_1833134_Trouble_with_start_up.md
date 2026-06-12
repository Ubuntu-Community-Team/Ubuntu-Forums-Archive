---
title: "Trouble with start up"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by boodah78 on 2011-08-25
I just installed Kubuntu 11.04 via wubi.  When i try to boot into Kubuntu it just hangs forever at the splash screen.  I am dual booting windows 7 ultimate and Kubuntu.  Plz help i really want to get to using Kubuntu

---

### Post by bcbc on 2011-08-25
what are your hardware specs? computer brand/model and graphics card.

---

### Post by boodah78 on 2011-08-26
MSI 760GM-P33 Motherboard 
AMD Phenom II X4 840 Quad Core Processor 
ATI Radeon HD 5450 Video Card
8 gigs of ddr-3 ram
1 tb hd

it worked with Ubuntu just fine i dont know why this is happening now

---

### Post by bcbc on 2011-08-26
I suppose you can remove the splash and see where it is getting stuck. If it's on the first reboot after windows (ubuntu installation) refer to [this]("http://ubuntuforums.org/showpost.php?p=10089820&postcount=8"). It shows how to add 'nomodeset' but you can also use it to remove *quiet splash*. 

Give that a go.

If it's the boot following the install, refer to post #1 of that thread.

---

