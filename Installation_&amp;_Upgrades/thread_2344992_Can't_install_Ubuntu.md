---
title: "Can't install Ubuntu"
date: 2016-11-29
forum: Installation &amp; Upgrades
---

### Post by dcpifhq on 2016-11-29
Hi
My pc is kinda a piece of poop, and I read somewhere in a forum, that Microsoft doesn't let you have an actual PERSONAL computer, and stuff.
Anyway, I wanna install Ubuntu, but when I click the "Install Ubuntu" button (the setup is not as it looks like on videos, it's a little bit different) my pc restarts into Windows 10 (yes I still have Windows installed), and if I try to repeat the same method, my pc does the same thing, even before it even gets the Windows loading screen.

Any answers would do.

---

### Post by oldfred on 2016-11-29
Is your Windows 10 from an upgrade from Windows 7 or Windows 8.
If from Windows 7 probably BIOS/MBR which then may have the 4 primary partition limit.
Either way you also may have Windows fast start up on which is hibernation. The Linux NTFS drive will not see hibernated Windows.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Post this from live installer:
sudo parted -l

---

### Post by dcpifhq on 2016-11-30
I changed my mind, since Microsoft requires you to BUY Windows 10 right now, I'm gonna just leave Windows 10.
I'm going to format Windows 10, and when Windows 10 boots up again, I'm just going to install UNetBootIn, and Visual Studio, and the rest of the memory is gonna be all on Ubuntu (and I'm also gonna leave an extra 20 GB just in case Visual studio needs to update).

---

### Post by oldfred on 2016-11-30
NTFS partitions really like to have 30% free inside them. At 10% free you just about cannot run a defrag as you have no working room.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

One user who must regularly get new computers, posted that with a new Windows computer he removes hard drive and installs SSD & Ubuntu only. Then system is fast. And then he can later sell system with Windows and not worry about any of his data as he never booted Windows at all.

---

