---
title: "Reinstall 7.10, save data?"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by snorkytheweasel on 2008-04-22
I boogered up something in Kubuntu 7.10. Now there is a problem related to Xserver (or so the system says). To get the machine useful again quickly: my boss insists upon having a GUI. So I need a good way handle this... fast.
[LIST]
[*]Is there a way to reinstall the OS without losing data?
[*]Is there a one-size-fits-all fix for display issues?
[*]What happens if I save data to a thumb drive that is FAT-formatted? 
I ask because I have had problems when 
[LIST=1]
[*]FTPing tarballs to a Windows file server
[*]FTPing back to LINUX and
[*]un-TARing. 
[*]The data were frequently corrupted.
[/LIST]
[/LIST]

---

### Post by Pumalite on 2008-04-22
Backup & Restore
Take your pick:
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by logos34 on 2008-04-22
> **snorkytheweasel said:**
> I boogered up something in Kubuntu 7.10. Now there is a problem related to Xserver (or so the system says). To get the machine useful again quickly: my boss insists upon having a GUI.

Xserver is failing to load at startup?  If that's the case, try running the interactive X config tool

sudo dpkg-reconfigure xserver-xorg

---

### Post by snorkytheweasel on 2008-04-23
> **logos34 said:**
> Xserver is failing to load at startup?  If that's the case, try running the interactive X config tool

sudo dpkg-reconfigure xserver-xorg

Bingo! Thanks ever so much.

**Warning to those who would attempt this process: **

It is pure, unadulterated ***[COLOR="Red"]HELL[/COLOR]***. There are many, many arcane questions to sweat through. I finally stopped researching and accepted each default answer ... and hoped. 

It turns out that (in my case) the default answers were good enough. 

KDE is now happy, my boss is happy, and I am unimaginably happy.

I just might name my first-born "xorg". :)

---

### Post by logos34 on 2008-04-23
Good to hear.  

Mark as 'Solved'.

---

