---
title: "Fresh install with Home Partition"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by saxuntu on 2008-03-19
I recently created a /home partition with a fresh install of Gutsy. I plan to upgrade to the Hardy RC when it comes out. I was just wondering if i should delete the hidden config files or just leave them? Any tips?

---

### Post by Herman on 2008-03-20
You're supposed to just leave them all there, that's probably the main reason why someone would bother creating a separate /home in the first place.

I prefer to dual boot and have a new Ubuntu install in one partition and an old Ubuntu install in the other, sharing a swap area. That doesn't take up any more room than having one install with a separate /home and I can safely try out Hardy well before it's officially released this way. Hardy is very nice, I'm typing to you from my Hardy installation now.
When I'm ready it will only take me a few minutes to transfer the needed files from one installation to the next, Hardy automatically mounted my old Gutsy install during the installation, so all I have do do is drag and drop. I'll be waiting until Hardy is released before I make it my main operating system though.

Regards, Herman :)

---

### Post by saxuntu on 2008-03-22
makes sense. I created the home partition mainly to preserve documents, pics, etc. And so i could dump apps and their dependencies that i experimented with and don't use.

Thanks

---

### Post by utUtu on 2008-03-22
> **saxuntu said:**
> makes sense. I created the home partition mainly to preserve documents, pics, etc. And so i could dump apps and their dependencies that i experimented with and don't use.

Thanks

A word of advise.  Better backup your data -pics, docs.  Not sure what you'll be using but some install will format partitions without asking.  Even if you are sure, better safe than later.
:guitar:

---

### Post by Herman on 2008-03-22
> makes sense. [COLOR=Red]I created the home partition mainly to preserve documents, pics, etc[/COLOR]. And so i could dump apps and their dependencies that i experimented with and don't use. I agree with utUtu, contrary to popular mythology, having a separate /home actually doesn't protect your data very much at all.
You still need to make a backup of your data to some other media as well.
Having a separate /home just saves you a few minutes of copying if you ever have to re-install.

---

### Post by Pumalite on 2008-03-22
Better to keep everything packed away in an external drive. So, if you have multiple computers is a snap to share docs.(faster than the speed of the LAN)

---

### Post by wRonG1 on 2008-03-22
What would you folks suggest as best back-up method ? Clonzilla , as on the "GParted-Clonezilla LiveCD" or "Clonezilla LiveCD' ? Just installed Ubuntu 7.10 and intend to save to an external drive _before_ I screw it up !

---

### Post by Pumalite on 2008-03-22
Take your pick:

[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by wRonG1 on 2008-03-22
> **Pumalite said:**
> Take your pick:

[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

WOW - Thanks Pumalite ! Didn't realize I had so many options - use True Image in Windoze as Ghost can't operate with more than 2 Gb RAM , apparently .

---

