---
title: "[SOLVED] 7.10 Error During update"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by freakypcteck on 2008-01-16
I am fairly new to Ubuntu,  i downloaded all the updates for 7.04 feisty so i can just run the update from update manager.  everything looks good at the beginning then i get this error "Error during update" (a problem occurred during the update. this is usually some sort of network problem, please check you network connection and retry.  the in the window a link is given.

Failed to fetch [ftp://ftp.videolan.org/pub/videolan/ubuntu/dists/sarge/main/binary-i386/Packages.gz](ftp://ftp.videolan.org/pub/videolan/ubuntu/dists/sarge/main/binary-i386/Packages.gz) Unable to fetch file, server said '/pub/videolan/ubuntu/dists/sarge/main/binary-i386/Packages.gz: No such file or directory  '


granted i am trying to run the upgrade from my wireless card, i do not see if it would be a difference if i run it from LAN card.  i am thinking everyone and there grandmother is trying to download the 7.10 upgrade, if someone could confirm that is the case then i will just wait to upgrade or i will just download the live CD and upgrade from there.

any help would be great :)

---

### Post by linuxwizard on 2008-01-16
You need to remove or disable all extra repos you added to your source list. Than try upgrading again.

---

### Post by freakypcteck on 2008-01-16
Dude that worked!  you da man!  upgrade is running now.  thanks

---

### Post by linuxwizard on 2008-01-16
You're Very Welcome, Glad to hear that it helped you and now upgrading. Please mark thread SOLVED
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

