---
title: "Xp/Gutsy Dual boot Real slow suddenly"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Jre35 on 2008-02-24
Hello,   
I installed Ubuntu 7.10 two weeks ago. Apart from a slower boot up than XP it works great. Recently, when booting up, my computer stays on the boot up screen for ~10 minutes. Then it takes an extra 3 minutes to load the screen where i choose to boot Ubuntu or XP. Ubuntu boots fine afterwards, but XP has problems, explorer.exe does not work, however i can run programs from the taskmanager, just not explorer, which depending on its mood, can start after 10 minutes or not start at all. I use Ubuntu >90% of the time so explorer.exe is not a big deal, I was just wondering what affected the long boot up as it never took so long before. XP used to boot up in under 3 minutes, and Ubuntu would boot in under 5. 

I have an 80 gb hard drive partitioned with vmware workstation 40/40 gb. 1 gb ram, and dual core 2 ghz amd processors.    
Also, I have an ATI mobility radeon x700 graphics card, but i downloaded the driver and it had worked fine up.

Thank you in advance.

Jason

---

### Post by pytheas22 on 2008-02-24
I had a similar problem where boot would take forever, and eventually I realized that if I reseated the SATA plug going from my hard drive to my motherboard, it solved the problem--I guess the connection was loose.  I don't know if this is your problem but you could check.

As for your Windows system, it sounds seriously messed up if it can't start explorer.exe reliably; you might want to check for malware.  It might also be a good idea to make sure your hard disk is not starting to go, which could be the source of a lot of strange problems; make sure SMART is turned on in BIOS, and there's also a utility you can run from Ubuntu to test a hard disk, although I forget the name.

---

