---
title: "Partition help"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by huviduc on 2008-03-10
When i partitioned my hard drive along time ago, i had different plans and didn't know as much as a know now. But either way, i made my root partition too small and its running out of space. I made my /home partition too big and its like wasted space cause i don't save anything there. I save all music and videos to my windows partition. So, my questions is, can i resize the two partitions with out losing any of my info? I have included a screen shot of Conky to show my hard drive partitions. I want to give like 5 Gig or so to the root partition and take it from the /home partition.

---

### Post by Pumalite on 2008-03-10
You can use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post a screenshot. Also post:
sudo fdisk -lu

---

### Post by Pumalite on 2008-03-10
If you work with partitions, backup everything first.

---

### Post by bigblue2sea on 2008-03-10
Definitely back up everything important. 

Even better, move the music, vids, pics, etc off the drive.  The partitioning process will go much faster if there is less data to move.

With 90 some percent of the root filled, data moving could be very slow.

---

### Post by huviduc on 2008-03-10
all the music, movies, etc are on the windows partition which i wont be touching. I only wish to sort or "give" 5 gig to the root partition from the home partition. I used this to back up
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)



 would i be ok to try the above idea?

---

### Post by LieToPurify3 on 2008-03-11
I'd say any time you're moving partitions around, back up your files.  I would think that even though your files are in your windows partition, which you won't be resizing, if your data is fragmented on your hard drive, resizing any partition might actually be moving more data then you think, which could potentiially end up in loss of files if it doesn't work properly.  just back everything up.  You should be backing up your data regularly anyway

---

### Post by housam on 2008-03-11
use Gparted tool and post a picture of the posision of your drives to enable us to help.

---

### Post by huviduc on 2008-03-11
here is a screen shot of my partitions. hda1 = winXP, hda2 = root, hda3 = home, hda4=swap

I back up all my stuff regularly. I am not worried about losing files, i dont want to lose all my settings and have to reinstall everything and attempt to get XGL+Beryl working, it took forever because of ATI.

---

### Post by Pumalite on 2008-03-11
From Gparted, right click on hda2 and choose resize from the menu. You have to expand to the right. It will take some time because a lot of files have to be moved. Make sure you backup everything first.

---

### Post by housam on 2008-03-12
> **huviduc said:**
> here is a screen shot of my partitions. hda1 = winXP, hda2 = root, hda3 = home, hda4=swap

I back up all my stuff regularly. I am not worried about losing files, i dont want to lose all my settings and have to reinstall everything and attempt to get XGL+Beryl working, it took forever because of ATI.

Using the newer version of Gparted , you can shrink hda3 from the lift side to the size you want leaving an unallocated space that you can add it to hda2 by graping the right side of hda2 to the end of the unallocated space.

---

### Post by huviduc on 2008-03-12
Would i have to boot from live CD.  I wont be able to do it while booted on my linux partition because it is mounted. Correct? I have a dapper CD, would that work?

---

### Post by housam on 2008-03-12
> **huviduc said:**
> Would i have to boot from live CD.  I wont be able to do it while booted on my linux partition because it is mounted. Correct? I have a dapper CD, would that work?

Yes , you have to boot from the Gparted live cd.

---

