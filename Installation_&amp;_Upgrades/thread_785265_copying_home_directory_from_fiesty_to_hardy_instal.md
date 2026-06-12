---
title: "copying home directory from fiesty to hardy install fails to transfer settings"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by genbuntu on 2008-05-07
Hi

I just made a clean install of Hardy ( with windows xp partition intact :) ). Previously I was using feisty (dual-boot with XP) .

 From what I had researched , I was convinced that preserving a copy of all the contents in my feisty /home directory  and then pasting it into the new (Hardy's) /home directory  would provide me with my original settings .
    However, after doing this , Ubuntu fails to load anything (except a xchat window , which I set to load at startup in my previous feisty installation as well).  It does not even load the panels at top and bottom , neither can I see any icons .  But if I choose the fail-safe gnome session  then it loads ,to some extent, some of the customization from my previous feisty install viz. panel icons , desktop files etc.. but I cannot start firefox , pidgin , use xchat etc. 

What am I doing wrong? Why am I not able to successfully migrate my settings from previous (feisty) version  to the newly installed Hardy and make it load successfully ?

N.B. : I had replicated the packages using "sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade"  command before I copied the contents of the /home directory.

EDIT:  oops! I just realized I made a spelling mistake in the title , should have been feisty  instead of fiesty. Any moderator may change that pls. thx.

---

### Post by genbuntu on 2008-05-08
So then I tried another idea : to copy home directory into a separate partition and then install Hardy over it , but that does not help either and it refuses to load the desktop/panels. 

Eventually, I made a clean install (formatted all ext3 partitions)  and am now in the process of copying relevant settings one by one whenever needed. For e.g. I copied Mozilla's directory and got my bookmarks etc back :) . Same with Pidgin and other programs I can think of now.

Its a tough approach but on the bright side I can get rid of all the extras I had previously which I don't need now :) .

---

### Post by HHelsinger on 2008-05-08
Can someone explain why just copying the /home directory wasn't sufficient.   I thought that that, and perhaps also copying the /etc directory was all that would be needed.  I'm reluctant to do a clean install until I understand this, and know how to replicate my current settings.

thanks.

---

### Post by PaulGrahamRaven on 2008-05-10
I'm curious about a similar upgrade path - in my case Gutsy to Hardy. 

Three partitions: 50GB /root, 148GB /home, 2GB /swap.

The reason I installed it that way is because the partitioning guides I had read suggested that having /home as a separate partition meant the actual core O/S could be upgraded with files and settings retained. Is this correct, and if so what's the best course of action? 

The [HardyUpgrades page in the community docs]("https://help.ubuntu.com/community/HardyUpgrades") suggests the network upgrade is recommended, but I've seen countless threads and posts here suggesting that a clean install is better. Which is correct?

---

