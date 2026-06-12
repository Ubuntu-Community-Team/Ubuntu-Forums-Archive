---
title: "Change Partition to Extended Partition without Data Loss"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by mjoerke on 2012-02-07
Hi, I'm trying to install Ubuntu on my laptop already running windows, but I just realized that a hard drive can only have 4 primary partitions (noob errors). I have a 500gb hard drive. The four partitions are the following: 1 Windows partition (450gb) with 300gb unused, a System partition from windows thats about 200mb, a 13gb partition labeled RECOVERY, and a 100mb partition labeled HP_TOOLS. I have no clue what the last two are, so I dont really want to delete them. I originally wanted to split the unused space from my main drive into a ubuntu system partition, and a partition for all my files to share over windows and ubuntu. However, I don't know how to convert that primary partition into an extended partition so that i can add those extra linux system and storage partitions inside of it.

I know this shouldn't be terribly difficult, I just can't figure it out and do not want to lose any of my data (that would SUCK)

---

### Post by Mark Phelps on 2012-02-07
Actually ... it IS very difficult to do ... without losing data.

You can't "convert" a Primary partition to Extended because the latter is just a container for other partitions.

You will have to end up REMOVING one of the partitions -- and the HP Tools is the most likely candidate.  You can start that process by copying the contents of the HP Tools partition into the Win7 OS partition.  However, realize that after you have done this, features available from the boot using Function keys may no longer work -- as you have moved the supporting files.

Then, I would use the Win7 OS Disk Management utility to SHRINK the Win7 OS partition.  Reboot into Win7 a couple of times after that to allow the filesystem to make any needed adjustments.

Then, you should consider backing up the now-shrinked Win7 install to an external drive.  To do that, download and install the FREE version of Macrium Reflect (MR).  Back up the Windows boot partition and Win7 OS partition to an external drive.  Then, use the option to create and burn a Linux boot CD.

At this point, you have the means to completely restore your current install of Win7, so basically, you don't need the Recovery partition anymore.

Then, I would checkout the Partition Wizard website.  They offer a FREE downloadable version you can burn to CD.  You can then boot from  that and use it to move your partitions to the "left" to have all your free space then on the "right".

After this, you have some free space and can install Ubuntu to that.

---

### Post by mjoerke on 2012-02-07
Hey thanks a lot man, but that sounds way too complicated and risky. I'm probably just going to end up running Ubuntu out of windows, not on it's own in installed partition. I don't want to go around deleting partition that I don't know what's in the and losing my data and/or warranty. However, couldn't I just copy the contents of my Windows partition to an external hard drive, delete the partition, make an extended partition and move the files over?

---

### Post by Quackers on 2012-02-07
I believe Fixparts (a programme written by srs5694, a member here) can change primary partitions to logical. It may be worth looking at.

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by oldfred on 2012-02-07
Good advice in previous posts.

how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

While not as fast as a full install to a internal hard drive:
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by mjoerke on 2012-02-07
I would delete the HP_TOOLS partition, I honestly do not need it (I know how to use the BIOS), but I really don't want to void my warranty. Also, Quackers, thanks for the link to FixParts, but, how do I use it? I really do not understand any of the description on the website.

---

### Post by Quackers on 2012-02-07
The section named "adjusting your partitions" explains how it can be done (within certain constraints). 
However any partition you intend to change to logical needs to be next to some unallocated space , in which you can create the necessary partition(s) for Ubuntu. I'm not sure that would be the case in your situation.
It is more straightforward for you to shrink the Windows C: drive (to create the unallocated space for Ubuntu to use) and then delete the HP TOOLS partition, thereby leaving only 3 primary partitions on the disc.
You should check first, but I'm reasonably certain that the tools which reside in the HP TOOLS partition can be downloaded separately from the HP website, if needed (which is not very likely).

You will then be able to install Ubuntu in the new unallocated space.

---

### Post by ottosykora on 2012-02-07
>I would delete the HP_TOOLS partition, I honestly do not need it (I know how to use the BIOS), but I really don't want to void my warranty.<

I have also simply copied the contents of the tools partition to an usb stick, then shrinked the main partition with windows own tool, then created the extended partition in the space now free and in that, the first partition is again one for the 'tools'.
Copied the tools back to it and all works. Even the in fact not much useful tools work as before as it is not relevant if this partition is primary or logical at all.
Other new partitions like those for linux come after the tool partition.

---

### Post by mjoerke on 2012-02-08
That's a great idea. I'm surprised I was too stupid to think of that. Well, I think I'll try that on the weekend when I have more time. Right now I've just installed it alongside windows, not on its own partition

---

