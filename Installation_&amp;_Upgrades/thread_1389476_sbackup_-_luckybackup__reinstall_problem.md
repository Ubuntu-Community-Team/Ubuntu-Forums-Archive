---
title: "sbackup - luckybackup  reinstall problem"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by eaglemystic69 on 2010-01-24
Hey Ubu's,

I will be as brief and detailed as possible!
Karmic 9.10 installed on a new HP G71

Backed up my whole system with sbackup and luckybackup onto a USB HD.  I  believe the includes and excludes were properly set. 

Then, had to create a dual boot system with windows7 recovery disks (for printer diagnostics), W7 is installed first.  Finally got them partitioned and booting properly. 

I have sbackup files:
2010-01-22_15.32.57.662779.cristo-laptop.inc
2010-01-22_14.46.39.693665.cristo-laptop.ful
sbackup states  "No backup found at target."

luckybackup had a  profile to restore then resorted to a blank default.  My /media/backmeup still has all the directory folders saved. Though no profile can be found.

I dragged and dropped /home (with all hidden files too) from my USB /media/BACKMEUP to the fresh /home folder and restored my personal files and (I guess) the application preferences found in the .dotfiles.

CAN I use these restore files on a system with different partitions than previously backed up from?  AND how do I restore these via either sbackup or luckybackup when their profiles do not recognize them? Can the LiveCD somehow work for a drag-drop method?  

I had this system loaded with Ubuntu studio and other apps I would rather not have to rediscover and install them on my slow internet connection.

---

