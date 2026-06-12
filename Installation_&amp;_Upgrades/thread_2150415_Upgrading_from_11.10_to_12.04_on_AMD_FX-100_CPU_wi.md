---
title: "Upgrading from 11.10 to 12.04 on AMD FX-100 CPU with nVidia GEForce card"
date: 2013-06-01
forum: Installation &amp; Upgrades
---

### Post by juanbuntu on 2013-06-01
Last year I installed Ubuntu 10.10, upgraded to 11.04, upgraded to 11.10 and I tried to upgrade from 11.10 to 12.04, but the upgrade process had numerous error messages, so I had to recreate the install/update sequence starting from 10.10->11.04->11.10 and did not have the courage to go again to 12.04 so I am still running 11.10 since last year. 


QUESTION: Is there a compatibility problem caused by having nVidia GeForce graphics cards with AMD CPUs?


Two weeks ago I burned the AMD64 version of the 12.04.2 .ISO image and booted the live system directly from the DVD. Everything seems to be running just fine. The live system recognizes all the the partitions and all the devices in the system (disks, video cards, nic, mouse, KB, etc), so here is the second question:


QUESTION: Is having successfully run the live system from the DVD a 'good enough' test?
Would you recommend that I take the plunge and upgrade to 12.04.2 from 11.10?


Thanks
juanbuntu

---

### Post by 2F4U on 2013-06-01
> QUESTION: Is there a compatibility problem caused by having nVidia GeForce graphics cards with AMD CPUs?


No. Your card should be supported by Ubuntu out of the box. You may be forced to use the open source drivers, however.

> QUESTION: Is having successfully run the live system from the DVD a 'good enough' test?

Successfully running the liveCD is usually a very good indication that your system will be supported by Ubuntu.

> Would you recommend that I take the plunge and upgrade to 12.04.2 from 11.10?


Yes, I would strongly recommend to upgrade since 11.10 is is EOL, so you won't get security updates.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by MartyBuntu on 2013-06-01
> **juanbuntu said:**
> 
Would you recommend that I take the plunge and upgrade to 12.04.2 from 11.10?


I'd recommend a fresh, clean install. Backup your data first.

---

### Post by juanbuntu on 2013-06-01
Well, I went for the upgrade, and I it looks that was a bad idea. [COLOR=#000000][FONT=Calibri]The upgrade shows 6 steps:[/FONT][/COLOR][B]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR][/B][B][COLOR=#000000][FONT=Calibri]1. Preparing to upgrade (went OK)[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]2. Setting new software channels (went OK)[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]3. Getting new packages (went OK. It took quite some time)[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]4. Installing the upgrades[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]5. Cleaning up[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]6. Restarting the computer[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri][/FONT][/COLOR][COLOR=#000000][FONT=Calibri]Started @ 02:15 PM and ended at 04:20 PM. Almost two hours for upgrading lots of libs and packages. 

Not bad at all.[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]
[/B][B]
[COLOR=#000000][FONT=Calibri]
[/FONT][/COLOR]

[/B]

---

### Post by efflandt on 2013-06-02
I recently upgraded the system on my SSD from 11.10 (originally installed fresh) to 12.04.2 (PC in sig). I started in the evening and thought it would be finished by morning, but step 4. stops at some points to ask questions. Other than that, everything worked fine. I had been using x-swat nvidia drivers, so before I did the upgrade I used ppa-purge to switch it back to regular nvidia drivers.

It was good that I had that alternate system on SSD when my main drive started failing and I could simply boot that system to e2fsck 12.04 on my main drive and lock out bad blocks.  But eventually it got worse and I transferred Win7, reinstalled 12.04.2, and copied my old /home to my main drive before I tried the upgrade on the SSD.

---

### Post by juanbuntu on 2013-06-02
When I was doing the upgrade from 11.10 to 12.04.2 the system asked me during step 4 (I believe installing libc-bin) to open the terminal and answer a couple of questions, which I did. 
It also asked me to select a config file for samba, MySQL and Apache (I chose to keep the config that I had). Other than that, the upgrade went quite smoothly.

---

