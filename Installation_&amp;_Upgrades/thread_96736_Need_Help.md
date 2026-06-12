---
title: "Need Help"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by skyhigh007 on 2005-11-29
I've an windows xp based pc and my hard has already partitioned into C drive and D drive. i install my xp under c drive and i want to install Hoary under D drive. During the installation, Net work Autoconfiguration Failed. so, i skip that step. when comes to partition disks, under the partion methods: Ease entire disk or manually edit partition table. Howcome it didnt detect my free spaces in d drive? what should i do ?

---

### Post by wrtrdood on 2005-11-29
Because it's not free.  As you say, the D: drive occupies that space.  You need to know what partition that is and then delete it if you want Ubuntu to use it.  This can be done using the partition tool.  Be careful here, though.  Don't delete the first partition which is going to be the C: drive.

BTW - I doubt that setting up the networking failed.  The default is to try to set the IP address through DHCP.  If that didn't work, the installer offers the chance to configure it manually.  Not a difficult thing to do but you do need to know something about what's going on to get it right.

---

### Post by skyhigh007 on 2005-11-29
what do you mean D drive is occupied? would it help if i reformatted? any partition tool that i can use?

---

### Post by linbetwin on 2005-11-29
Even if your D partition is completely emty (has no files on it) it doesn't count as free space because it has a file system on it (probably NTFS if you have Windows XP) You need to delete that partition. Choose "Manually edit the partition table" and you'll see two partitions. They won't be named C and D but is is probably the first in the list. Don't delete it. Select the second partition, press ENTER, select "Delete partition" and press ENTER again. Now you'll see a list with your C partition and FREE SPACE. Select the FREE SPACE, press ENTER, choose "Automatically create partitions" or sth. like that and you should be good to go.

---

