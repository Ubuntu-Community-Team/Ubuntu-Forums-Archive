---
title: "Problem installing ubuntu along with windows 7"
date: 2011-07-08
forum: Installation &amp; Upgrades
---

### Post by varunit on 2011-07-08
Hello friends, I would like to install ubuntu along with my already existing windows 7 OS.
[IMG]http://imageshack.us/photo/my-images/707/parions.jpg/[/IMG][http://imageshack.us/photo/my-images/707/parions.jpg](http://imageshack.us/photo/my-images/707/parions.jpg)
[IMG]http://imageshack.us/photo/my-images/707/parions.jpg/[/IMG]
The above image is my current partitions scheme. I would like to install ubuntu in the My Stuff partition.. I would not like to lose my data.. Please help me installing ubuntu without losing any data.. Thank you

---

### Post by oldfred on 2011-07-09
You have some choices. You can install wubi, which is a test version for windows users to try Ubuntu. It is for a longer trial than just using liveCD but is not intended as a permanent install. It is easily uninstalled and does not require repartitioning.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

Whatever you do be sure to have good backups.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

A full install to separate partitions gives you full dual boot. If you have issues in the windows partition you can still boot the full install, where with wubi it depends on windows NTFS partition to work.

How much space do you have in D:? NTFS partitions like 30% free to keep working well. You can shrink D: with the windows MMC and make room for Ubuntu's partitions. Do not create partitions with windows partition tools, use Linux's gparted.

Version 10.10 has some confusing instructions that was easily misinterpreted and overwrote the entire drive. If installing 10.10 ask for even more help. Older and newer versions are more clear on installing. 

Herman's guides are very detailsed, not as complex as it may seem due to detail.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by zero244 on 2011-07-09
I bought a laptop with Windows 7.....and between Windows and HP they took all four primary partitions.
Which prevented me from creating space for Lucid.
If I would of had a full feature disk management program in 64 bit I could of gotten around it, but I didn't.

So I just removed Windows 7 and went full drive install of Ubuntu Lucid and glad I did.

The disk management that comes with Windows 7 premium is a joke and almost worthless.

---

