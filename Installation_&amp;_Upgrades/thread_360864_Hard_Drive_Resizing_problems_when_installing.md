---
title: "Hard Drive Resizing problems when installing"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by Missyme on 2007-02-13
I was trying to install Ubuntu on my Compaq laptop which also runs XP.  During the "Prepare disk Space" window, I first chose the "Resize IDE1 master, partition #1 (hda1) and use freed space"  When I pressed forward, the mouse pointer became the spiral but it did not do anything else.  I left it like this for probably around 30 minutes and there were no changes.  I then tried to manually edit the partition table.  I followed the instructions from 
[http://ubuntuforums.org/showthread.php?t=354023]("http://ubuntuforums.org/showthread.php?t=354023")
as well as [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")

My hard drive has 60 gigs, 14 of which are full.  I decided to try to resize the partition to 32 gigs, and then add the swap and ext3 partitions.  
I got the following error:
An error occurred while applying the operations
The following operation could not be applied to disk:
Resize /dev/hda1 from 55.88 GiB to 31.47 GiB
See the details for more information

details:
check filesystem on /dev/hda1 for errors and (if possible) fix them
 
I also tried to resize the partition from GNOME partition editor and I got the same error.

Before I tried to install ubuntu, I defragmented my harddrive and there were two bars of unmovable files.  I'm not sure if that might be the problem.  

Thanks in advance for any help and let me know if there is any more information I could give.

---

### Post by Kateikyoushi on 2007-02-13
Those unmoveable files might be a problem if they are located in the secondhalf of the disc what I assume is the case. 
You could try to disable swap file and re enable it in windows, because swap is unmoveable but if yo recreate it might bring it closer to the beginning of the disc.
Other option is to leave the windows partition bigger try 45GB or so.

---

### Post by Missyme on 2007-02-13
I tried to make the partition 45 Gigs and there was the same problem.  I also tried with 53 Gigs and no difference.  

I'm not sure whether the diagram that is shown with the defrag is accurate on the position but the first of the unmovable files was on the left and the second one was in the middle.

---

### Post by Missyme on 2007-02-15
I was able to fix this and Ubuntu is now installed :) 

If anyone else has this problem, here is what I did:

I tried removing the swap file and defragmenting several times but it didn't help.

I got a newer version of Gparted from [http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")
(The one that comes with Ubuntu is version 2.5 and they have 3.3 out now.)  I used their LiveCD download.  

I booted the computer with the Live CD and tried to make the partition smaller, and was unable to, but the error message was more useful and told me what to do run "chkdsk /f"
I booted back into Windows and ran that from the command and the next time I restarted my computer it ran.  

After that I used the Gparted Live CD again and was able to change the partitions with no problem, and installed Ubuntu.

If anyone else runs into this I hope it helps.

---

