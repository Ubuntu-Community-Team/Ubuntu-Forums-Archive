---
title: "removing windows"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by uberdonkey5 on 2008-10-08
I have dual boot (ubuntu / vista) and want to wipe windows of completely to have just ubuntu computer. However, I have made many modifications to my ubuntu system and don't want to reinstall it.

I have a fear of 'mount points', but would like to free the space for just ubuntu (and in a neat way, with same file system). Is there any way to do this simply? Also, would this boot slower than a completely fresh reinstall, or are there other potential drawbacks?

of on hols soon, so may not reply immediately, but thanks in advance to any tips.

ud5

---

### Post by pytheas22 on 2008-10-08
I'm not sure of your specific hard disk geometry, but if you have a normal set up (Ubuntu on one partition, Windows on the other, swap somewhere in between), your best bet is probably to boot to the Ubuntu live CD, install the program 'gparted' by finding in Synaptic or typing at a command line:

```
sudo apt-get install gparted
```

and then starting the program by typing:
```

sudo gparted
```

gparted will show you the existing partitions on your hard disk.  You can select your Windows partition (should be obvious because it will be the only one formatted in NTFS), then choose to delete it.  Next, choose your Ubuntu partition, and click the 'Resize/Move' button.  Resize it so that it occupies all of the space on your hard drive that was freed by destroying the Windows partition.  This way, after you reboot, everything on your Ubuntu system should work as before, except it will have more disk space.
[B]
Please note that modifying partition tables always carries an inherent risk, so you should back up all important files (and if possible your whole Ubuntu system) before attempting any of these operations.[/B]

Also note that you have to run gparted from a live CD; it won't work from your Ubuntu installation because it can't operate with partitions that are currently mounted.

---

### Post by uberdonkey5 on 2008-10-08
thanks, seem to have problem with gparted though... just shows 'unallocated (and unallocated filesystem) 232 GB.

I have dell media centre partition (5GB?) and NTFS windows partition. HD is 260GB I think, so what is being shows is either completely wrong or the ubuntu partition only (and even then, it can't recognise the file system)?

Just remembered abuot this Dell 'media direct' partition, which has always been a pain, but presume I can just do the same with that partition too... if I could find it.

---

### Post by topalof on 2008-10-08
The easiest would be to just reformat it with another filesystem type. Where does your fear of mount points stem from? It's not a problem to mount the new partition per default every time you boot the system, that way you wouldn't have to worry about mounting it by hand, if that is your problem.

---

### Post by pytheas22 on 2008-10-08
The information you're getting from gparted seems strange.  Could you please post a screenshot?

---

### Post by uberdonkey5 on 2008-10-08
here goes...

(PS. there are no other devices I can select)

thanks :D

PPS. I have considered just a reformat anyway (to xfs filesystem type.. I love speed)

---

### Post by cariboo on 2008-10-08
You can use gparted while you are running ubuntu on the same hard drive that you want to modify. Use the LiveCD to repartition your hard drive.

Jim

---

### Post by pytheas22 on 2008-10-08
That output is really weird.  As the poster above suggests, please try booting to a live CD.  Once you're logged into the desktop, you'll have to install gparted by typing:
```

sudo apt-get install gparted
```

Do you get the same results there?  You can't edit partitions on a system that's running, but it should be able to at least display information about the disk structure, so it's strange that it's not.

---

