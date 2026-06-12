---
title: "Quick Installation Question"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by Jalhalla on 2006-12-23
Well, I'm new to this and I've looked around the site and in the forum, but cannot seem to find an answer, so here goes nothing:

I have two 40GB HDDs in my computer, both NTFS format. Master has WinXP Home installed. The other is simply for more storage space for music and DVD rips.

If I were to install Ubuntu on either, would my data be lost? I want to replace Windows (finally), but don't have enough room to put data on the slave. So, will Ubuntu installation re-format and delete what I have on my disks?

Thanks again. :-({|=

---

### Post by taurus on 2006-12-23
If XP is on the master drive while all your music on the slave drive, then better use gparted from the LiveCD to resize the master drive, leaving some room at the end to install Ubuntu then!

---

### Post by Jalhalla on 2006-12-23
Uh... Explain that again for me? =D

---

### Post by taurus on 2006-12-23
Boot with the LiveCD, then from the System -> Administration, you will see a program that says something like Gnome partition or something similar to that.  Click on it and point it to your first harddrive, usually /dev/hda1 (if you have a IDE drive).  Then, tell it to resize the drive and leave whatever the amount of space want at the end...

Here are some screenshots if you want to look at them!!!

[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

---

### Post by Jalhalla on 2006-12-23
I have less than 4GB left on the master.

I also want to replace Windows with Ubuntu.

And, can I access my slave drive through Ubuntu, even though it's a different drive format? (NTFS).

---

### Post by taurus on 2006-12-23
Yep.  You can mount and access your slave even though it's ntfs.  Here's a guide on how to do it.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jalhalla on 2006-12-23
Well, that guide made NO sense what-so-ever.

But, you've been mighty helpful.

I'll go find a beginners guide in laymen's terms.

---

### Post by taurus on 2006-12-23
Then why don't you install Ubuntu on the master drive, wiping out XP, first and I will walk you through mounting the slave drive, ntfs, then!!!

---

### Post by Jalhalla on 2006-12-23
With doing this, it will erase all data. And I don't have enough room to backup.

I'll leave this for now and come back when I have a bigger HDD. ;)

---

### Post by taurus on 2006-12-23
Okay.

---

