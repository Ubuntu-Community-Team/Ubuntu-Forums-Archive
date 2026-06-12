---
title: "Dual boot sticky thread please!"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by mtdave on 2010-05-03
It would be nice to get a sticky thread up for dual boot installation issues. It seems like this is a very common problem with the upgrade from 9.10 to 10.04.
 
I was finally able to solve my issue dual booting 10.04 and Windows XP Home at this thread.
 
[[FONT=Consolas][SIZE=3][COLOR=#800080]http://ubuntuforums.org/showthread.php?t=1469724[/COLOR][/SIZE][/FONT]]("http://ubuntuforums.org/showthread.php?t=1469724")
 
I had to reinstall Grub2 and run update-grub.
 
Then I had to run Rescue on my XP disk. Once to the DOS command line I ran the following command:
 
C:\Windows>fixboot c:
 
I rebooted and now all is well. I can boot to Ubuntu 10.04 or Windows XP from my Grub menu.

---

### Post by dino99 on 2010-05-03
[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

