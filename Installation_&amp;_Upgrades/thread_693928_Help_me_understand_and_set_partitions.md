---
title: "Help me understand and set partitions"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by glo on 2008-02-11
Hello everyone. I'd like to install Ubuntu on my desktop pc after letting go of mswin. I used to have a ghost backup image of my C drive stored in D. That saved me much trouble at the time. So I read [http://ubuntuforums.org/showthread.php?t=360283](http://ubuntuforums.org/showthread.php?t=360283) and it looked familiar.

I currently have two hard-disk drives on my pc: 20gb and 80gb both will be formatted before I install Ubuntu.

Besides what is needed for the system, I want to have another partition to hold data the such as documents, music, videos, along with a partimage backup image of my system. When things fail and I need to start over, I will simply be able to boot system rescuecd and have my Ubuntu rolled back to exactly as it was, but still retain my data files.

If this is possible, please suggest me a partition setup that will suit my needs, and how would I go about to install Ubuntu on the selected partition and link the data partition etc.

Thanks,
glo

---

### Post by codeslicer on 2008-02-11
You're formatting both hardrives? Which ones have Windows and your files on them?

---

### Post by Pumalite on 2008-02-11
Install your system in the first drive ( 19 GB for '/' and 1 GB for /swap). Make a /home partition of your 2nd drive. There you can store anything.
I'd use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Install Ubuntu, go Manual and use the partitions already created.

---

### Post by codeslicer on 2008-02-11
You don't need the GParted livecd, the Ubuntu LiveCD contains GParted by default in System->Administration

---

### Post by Pumalite on 2008-02-11
The Gparted Live CD is a newer version, more powerful and more flexible. Easier to use too.

---

### Post by glo on 2008-02-11
Thanks for the useful suggestions.
All my important files are already backed up on removable media. Both my HDD will be formatted so it isn't a problem.
I will try the above now!

Thanks again,
glo

---

### Post by Pumalite on 2008-02-11
Good luck!

---

### Post by glo on 2008-02-11
I did what was suggested and now am running Ubuntu.
When I tried to mount my hda1 (80gb Ubuntu's /home folder) under system rescuecd, it was empty and there was nearly no free space available. Am I doing something wrong?

---

### Post by Pumalite on 2008-02-11
Explain to me what you did, step by step.

---

### Post by glo on 2008-02-11
What I did:

1.
Boot rescuecd and setup my hdds as follows:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux
/dev/sdb1               1        2237    17968671   83  Linux
/dev/sdb2            2238        2498     2096482+   5  Extended
/dev/sdb5            2238        2498     2096451   82  Linux swap / Solaris
```

2.
Installed Ubuntu after choosing sda1 for /home sdb1 for / and sdb5 for swap.

3.
Boot into rescuecd,
```
mkdir /mnt/backup
mount /dev/sda1 /mnt/backup
partimage
```
at around 5% partimage complained there's not enough space available. when I ls /mnt/backup I saw listed only my incomplete image file.

---

### Post by Pumalite on 2008-02-11
Start again. Boot Gparted live CD. Delete everything in your hard drives. Make a new partition in your first hard drive aprox 19 GB, mount point '/'. Make another partition with the rest of that hard drive, mount point '/swap'. Make a new partition of your whole entire 2nd drive, mount point '/home'
Install Ubuntu; go Manual and use already prepared partitions.

---

### Post by glo on 2008-02-12
I did it again, and it works!
Time to welcome another convert :)
Thank you all so much!

---

### Post by Pumalite on 2008-02-12
Youc are4 welcome.
[http://www.unix-tutorials.com/go.php?id=861](http://www.unix-tutorials.com/go.php?id=861)

---

