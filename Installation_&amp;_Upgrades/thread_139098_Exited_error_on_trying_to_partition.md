---
title: "Exited error on trying to partition"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by cactusbin on 2006-03-03
Ok heres my story, I was running a server for a personal website (very small) and also running eggdrop xmail and an ftp and ssh server, but I was running all this on my personal computer, as you can imagine it slowed all my work down, but to my luck I found an old computer in the basement it has 3 GB of HD space and 64 MB of ram running windows 98. I thought I could make this into a server, so I bought a wireless adapter forgetting that I need SE to make and adapter work, so I thought, I can use linux its more reliable anyway, on my personal computer I am running linux so I'm familiar anyway. So I tried Fedora Core 4 (like I have on my personal computer) and it didn't work, I tried Debian, and I got it installed but I wasn't very familiar with navigating EVERYTHING with the command line, so I stumbled upon Ubuntu! I tried to install it under regular install (because I'm assuming server doesn't give me KDE or GNOME or any graphical GUI) and everything goes fine untill it starts up the partitioner. It exits to the command line and either displays a string of text then Segmentation error over and over, or it displays Exited over and over. Whats wrong?

---

### Post by rmjokers on 2006-03-03
Not sure exactly what is wrong, but I have a few suggestions:

1.  Make sure that the CD you burned was written properly by verifying its checksum or just burn a new copy.  A bad CD would give you strange behavior like this.

2.  Try using the Ubuntu live CD on the system first to make sure it works ok with your hardware.

3.  Take a look at some distros made for older systems.  Something like Damn Small Linux might be more suitable for the system you mentioned.

4.  If all else fails, try to do a slow format of the disk drive to make sure it doesnt have any bad sectors (this could also be the cause of your partitioning problems).

---

