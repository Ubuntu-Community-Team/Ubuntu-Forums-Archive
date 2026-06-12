---
title: "The power of Failure"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Omegus on 2011-01-13
Hey everyone long time Ubuntu user first time post. Until now. Ok here are the spec for a brand new computer i ordered at Ibuypower.com.

Optical drive : Sony 24x Sata DVDRW
Powersupply: Xion 700W
Harddrives: 2x WD 500GB SATA-2 WD5000KS
Motherboard: MSI 890GXM-G65
Videocard: Radeon HD5850 1GB
Ram: 2x 4GB DDR3-1333 Single
Processor: AMD Phenom II x6 1055T Tray
Raid setting: Raid-0 

Anyways I live for Ubuntu but my problem here is when I finish partitioning my Hard drives i set 50GBs to Ext4 journaling file under "/    " and the rest was for swap. (now this is the first time I have done a manual partition. Also super excited to get Ubuntu 10.10 going and this bad boy.)
after I set the partition I went through all the settings timezone, keyboard then finished putting in my username and password. After the files "Finished copying" it said "its up to you now" but it would not let me click on next. this is where i'm stumped, I tried running the installation again but same problem I tried redownloading and burned a new cd but same thing. Did I do something wrong in the partition? or is it something else?

Now I cant make love to you but if

---

### Post by Quackers on 2011-01-13
Did you use a capital letter in the username field? No capitals allowed there. Or did you get past that screen?
Also raid0 may be a problem if it came with your pc and is controlled by your bios.

---

### Post by Omegus on 2011-01-13
Wow I feel like such a tool....Thanks so much , it worked of course. Again thanks and now ill kick myself for something so simple stumping me like that.

---

### Post by Quackers on 2011-01-13
No problem :-)
See how the raid thing goes. I think grub may be a problem. There are users on here who know about these things. Maybe one will be along some time :-)

---

