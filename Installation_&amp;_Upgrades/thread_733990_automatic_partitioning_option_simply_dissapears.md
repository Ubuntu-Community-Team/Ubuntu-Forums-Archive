---
title: "automatic partitioning option simply dissapears"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by chumchum on 2008-03-24
Hello all
I tried installing a ubuntu gutsy/WindowsXP dual boot,but to no avail, he "manual" partitioning tool was just so horridly complicated for someone quite so new as me, so I've decided to opt for the automatic one, from the live CD installer (the one with a slider, where you resize your windows partition and the installer automatically creates a root and swap and the installs).
So I select this option, use the slider and reduce XP's partition's size by a bit less than a quarter using the slider, and click on forward, instead of beginning the installation it brings me back to the partitioner (step four) displaying all the option, except the top option, simply dissapeared and I must chose between 
"guided- use entire disk
  -SCSI1 (0,0,0) (sda)- 160.0 GB ATA ST3160021A
  -SCSI5 (0,0,2) (sdd)- 1.0 GB GENERIC USB Storage-SDC"
"Guided -use largest continuous free space"
"Manual"
I've searched the forums and I see someone else has had a similar problem, however they had an error message, I have no error messages whatsoever, the person in question solved there problem by defragging multiple times from within Winows, I tried the same, but that didn't work.

Can anyone please help?
Thanks beforehand.

---

### Post by forestpixie on 2008-03-24
I would partition before the install - you can use the tool in system >admin - partition editor - it is quite simple to do. 
This thread goes through the whole thing from beginning to end - in addition have a looka t psychocats page - should be more than enough information, if you have a question after you've looked at them - post back.

[http://ubuntuforums.org/showthread.php?t=732108](http://ubuntuforums.org/showthread.php?t=732108)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by chumchum on 2008-03-24
Well I realized that the reason it isn't working is because the windows NTFS partition is "locked" I made another thread about this and have yet how to figure out how to make it allow editing.
thanks for those links ;)

---

### Post by forestpixie on 2008-03-24
I think that you might find you need to chkdsk the win partition.

---

### Post by rosegarden78 on 2008-03-24
I stopped using partitions because VirtualBox runs a virtual machine with USB support.  You can install VirtualBox in Windows and then run Ubuntu on top.  Or use Ubuntu Studio as the host with a Windows XP virtual machine.  As far as manual partitioning here what you need:

1) One partition for use as EXT3 with the mount point as /
2) One partition for use as swap (double your RAM)

Hopefully all is well your installation went smoothly.  If you choose use entire disk your Windows is gone.  It took me six months to get fully acclimated to the Linux computing environment.  These forums and others are a great help.  But knowledge is only half the battle it takes experience to become proficient.

Related articles:
[http://ubuntuforums.org/showthread.php?t=277684&page=2](http://ubuntuforums.org/showthread.php?t=277684&page=2)
[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)

__________________

---

