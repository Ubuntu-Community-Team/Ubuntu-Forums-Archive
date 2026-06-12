---
title: "Neither Ubuntu nor Xubuntu Live will load"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by cdg110 on 2008-02-22
My System is a Compaq SR1920NX, AMD Athelon 64+ 3500 2.2 GB processor, 512 MB Ram. 120 GB Samsung SATA HD, HP CDrom drive, No floppy drive. 
CDs are good, both verified on another system and they both boot properly there, just not on my system.  Both CDs are version 7.10
On my system, the memtest86 runs fine from the menu, but when I select the install or the CD verify, it loads the kernal, then I get the Ubuntu splash screen but no activity of any kind.  The activity bar remains dark. I do not receive any error messages, Just end up with a hung system. I have swapped out the CD drive and the IDE cable to the CD drive. 
I have also run complete PC Doctor Diagnostics (from Compaq) on the PC, and it passes every time without any errors. 
I have Win XP home loaded on the HD, I wanted to explore Ubuntu using the Live CD feature. I have installed and used RH Linux before, but this is my first time using Ubuntu distro Linux via Live CD's. Any thoughts ? 
2/23/08 Replaced ATX power supply, as a test. No change in symptoms.

---

### Post by carlosfocker on 2008-02-23
Sounds like video driver issues.   You should be able to boot the live CD to a prompt and configure your drivers but this may be more then you want to get into at this point. If you want you can try to install by downloading the Alternate CD and using text mode install. 

This link has some information to help you along.  The cd's should be on the Ubuntu site under downloads.

[https://help.ubuntu.com/community/Installation/I386]("https://help.ubuntu.com/community/Installation/I386")

---

### Post by RJ Hythloday on 2008-02-23
I recently reinstalled and the live cd that had worked once and let me install wouldn't. I physically removed my agp and everything was fine. I still haven't reinstalled my agp though.

---

### Post by Partyboi2 on 2008-02-24
What happens if you boot without the splash screen? At the main menu press F6 and changed the word splash to nosplash and then press enter to boot.

---

