---
title: "[SOLVED] System back up"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Dyffo on 2008-10-10
I have Ubuntu Hardy, and am going to upgrade to Intrepid, before doing this I would like a back up of my files - is there a simple way of doing this.I tried to install "backuppc" but this requires "apache" w2hich I can't find anywhere. I aqm particularly concerned about losing my Virtual Box and the associated data. If I could just back this up alone it would be O.K

---

### Post by Rocket2DMn on 2008-10-10
Moved to Installations & Upgrades - please don't post support questions in the Tutorials & Tips forum.  Threads there require staff approval and are for Guides and HowTos old.

Remember that Intrepid is still a development release and subject to breakage.  If you are running Ubuntu IN vbox, then I wouldn't upgrade, since afaik, Intrepid still doesn't work in vbox.

I use Simple Backup (sbackup) to make backups of my system.  The biggest thing I have against it is that it compresses the backups with gzip, which means it's not as feasible for large backups, esp. when most of your stuff is already in a compressed format like images, videos, and music are.

---

### Post by Pumalite on 2008-10-10
Use Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by WWSmith36 on 2008-10-10
I´m a big fan of disk imaging for system backup.  The only problem is you can´t run it on a mounted partition.

I run it from LiveCD.  
First I enable universe repository.
Then

```
sudo apt-get update
sudo apt-get install partimage

partimage
```

Hope this helps

---

### Post by Dyffo on 2008-10-11
Hi thanks - I used "sbackup" seems to be fine. I had a look at "clonezilla", my problem is that I don't have a high capacity USB facility, and cd's are not an option !. Also had a look at " keep" but in the end decided on "sbackup".
I will now go for the Intrepid upgrade. This is not in vbox but on my main system. I only use vbox for Windows as a last resort !!!

P.S Sorry about the incorrect posting - I just noted the "How To" and thought that's for me !!

---

