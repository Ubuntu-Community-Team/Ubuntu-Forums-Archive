---
title: "Restoring a separate /home partition"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Dritz on 2007-10-19
So sometime during Dapper I moved my home partition to a separate partition since I knew it may come in handing if an upgrade failed or I wanted to try another distro or something. Well my Gutsy upgrade didn't go so well so I'm either going to be going to do a clean install of Fiesty or Gutsy. Honestly I'll be going with whichever one works best.

Anyways my question is: "Are there any risks in using a previous /home directory with a fresh install". Also since I'll be doing a fresh install would there be any problems with me deleting some of the hidden application folders in my home directory?

Also it's been sometime since I've moved partitions around. Could someone post a link to a fairly recent (hopefully (k)ubuntu focused) on how I'd go about restoring my home partition?

---

### Post by monado on 2007-10-20
There shouldn't be any risks as long as you select to keep the partition (as in don't format it). On the other hand some of those deleted folders may have contained application settings, so you may experience inconvenieces (grammar?) if you deleted the wrong stuff.

I didn't quite understood "restoring my home partition". If you ment setting it up durring Gutsy/Feisty installation so it's accesible and usable then it's easy: when you get to the partitioning step, select "configure manualy", then select your /home partition (enter in text-mode installer). There, first of all, make sure "Keep existing data" is selected. Secondly choose the mount point as "/home". If in a text-mode installer (don't know about the GUI-sh one) select "Done setting up this partition", and continue with the installation.

Also it's very important to set a user name exactly as the folder on your /home partition is called. For example if your user name was "dritz", during installation it should also be "dritz".

Good luck.

---

