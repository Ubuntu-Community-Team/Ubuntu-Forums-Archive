---
title: "What did Gutsy do to my windows partition?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by dschmier on 2007-10-21
I'm struggling with my attempt at installing Gutsy from the CD.  Note, I previously had Feisty installed and used the recommended upgrade method.  Because I have an ATI graphics card, that broke my X and I was only able to get it half working by following any of the many guides to getting ATI cards working.  I'm almost sure that had to do with a conflict between something new that Gutsy installed and something that I had previously installed when trying to get my graphics card working with a previous installation.  So I decided the best fix would be just a clean install of Gutsy.  I backed up my documents from my linux partition onto my windows partition (I know, not much of a backup, but it has worked for the installation of every release since Hoary).  

During the Ubuntu installation I got to the partitioner and set up the partitions as usual (again, as I have for every installation since Hoary).  I have an ext3 partition for Ubuntu, plus a swap, an NTFS partition for windows and then two other small partitions (one is fat16 and one is fat32) which are, I believe, Dell Utilities (the machine is a Dell) and I have never been able to figure out exactly what they're there for, but I'm afraid to delete them.  I told the partitioner to format the ext3 partition and mount it at "/" and to leave all of the other partitions untouched (but to mount the NTFS partition at "/windows").  Once running the partitioner I got an error that I've never seen before, though, which is that the partitioner found unexpected cluster sizes on one of the FAT partitions (2k clusters instead of 1k clusters, I think).  It asked me if I wanted to ignore this and continue or cancel, so I decided to cancel and try to figure out what was going on.  If nothing else, then I could at least back up my windows partition before messing around any further.  I guess the installer had messed with GRUB, though, because upon restart, I got a GRUB error (I think 15).  I remembered from previous mistakes that I could use my Windows XP disk to overwrite the master boot record which would at least allow me to get back into Windows.  So I used "fixmbr" on the Windows XP disk but unfortunately that just left me with an error on startup that says "No bootable device found."

So where do I go from here?  I have since found out that there is another command in the Windows XP recovery console called "fixboot".  Should I use that?  I basically just want to get back into Windows so that I can back everything up, then I wouldn't care what Ubuntu did to the partition table.  Or would I be better off sticking with the Ubuntu installer and trying to get that to work so that I can get GRUB working and get back into windows that way?

I know I should have been a little more careful and backed things up before I got to this point, but, again, I've done this so many times over the past two and a half years and I've never run into this problem before.  I know the windows partition is still intact -- it certainly didn't format anything -- I just don't want to do anything stupid and lose what's on there.

Any suggestions?

---

### Post by Pumalite on 2007-10-21
Use Super Grub and check to see if there is some Windows left:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

