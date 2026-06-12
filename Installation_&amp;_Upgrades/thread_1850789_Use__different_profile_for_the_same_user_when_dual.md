---
title: "Use  different profile for the same user when dual-booting."
date: 2011-09-27
forum: Installation &amp; Upgrades
---

### Post by blastfm on 2011-09-27
I would like to ask for help.
I am currently dual-booting my laptop (HP G4-1025tx) with Ubuntu 11.04 and UbuntuStudio 11.04.

When I installed UbuntuStudio, I made it use the same /home folder and same user account so I can access my files from both, since i will be working on them from either distro. I ended up with UbuntuStudio automatically retrieving my account settings (theme, wp, startup apps, etc) from the Ubuntu install. This caused some minor troubles, since I am using Unity on the Ubuntu install, and basic Gnome2 on the UbuntuStudio, the theme went whacked. Also, the Startup Application is the same for both, but I have several apps and scripts I have set to start in Ubuntu that I dont want to startup or are not installed in UbuntuStudio. 

Is it possible to make each (Ubuntu and UbuntuStudio) use the same user but set them to use different profile settings (i.e. startup apps, theme, etc)?

Thank you.

---

### Post by SecretCode on 2011-09-27
I think not. As I see it, having a common home folder is good for upgrading / reinstalling, but with dual boot, you'll get the problems you've found.

What I suggest is creating separate /home folders, each of which will then have its own /home/username folders with separate app settings ... but then linking the main subdirectories (Documents, Music, Pictures, Downloads etc) to common places.

I haven't done this myself (yet - often thought about it) and I'm not sure if symlinks or hard links would be best (or even mount --bind / mount --move).

---

### Post by oldfred on 2011-09-27
I have used symlinks to folders in my data partitions. Works best if all Debian based. But others suggest bindfs for networking issues and some other potential issues.

Splitting home directory discussion - oldfred's details in post #4:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

