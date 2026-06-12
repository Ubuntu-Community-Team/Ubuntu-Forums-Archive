---
title: "dparted problems"
date: 2006-09-29
forum: Installation &amp; Upgrades
---

### Post by gen_maximus on 2006-09-29
I had a dual boot system with winxp (one hard disk), so today i decided to remove my windows partition and use the extra space for my home directory. I used gparted and moved my root to the begining of the disk, and then i put my /home right after it. i was left with about 40gigs of unallocated space on the end of the disk. 

I booted with the live cd and then resized my home directory to use the unallocated space. Now when I boot up I can only see about 350mb of free space and it says that 50gb/51gb is being used even though there was only 19gb of data to start with.

Is there any way to fix this problem or did i completely mess up my drive?

Thanks

---

### Post by cotcot on 2006-09-29
No I do not think there is a problem.
You extended the /home. Gparted will use the maximum number of blocks on the disk, leaving 350 MB. 350 MB is less than a block so it could not be used. 50/51 is a rounding issue.
So you do not have a problem.

---

### Post by gen_maximus on 2006-09-29
What happened was, my /home was about 19gb and i had about 32gb of unallocated space. I extended the /home so i would be left with about a 51gb home directory. But the system now reads it as 98% full, when in reality, it should only be about 40%.

edit: to be more clear, nautilus reads /home as 18.6gb/19gb full while gparted reads it as 50.6/51gb full. It should only be 19.6/51gb.

---

### Post by marcelm on 2006-09-29
When making a dual boot XP - ubuntu , i would personally advise to re-partition in XP, using a good partition manager. Before launching the live CD.
especially if one uses ntfs.

---

### Post by Herman on 2006-09-30
I believe GParted is already the very best  partition  manager you can get, and it's 100% compatible with Ubuntu. It can handle NTFS without any problems.  You are talking about one of your Ubuntu ext3 partitions though, aren't you?
I have had older versions of GParted mis-read or mis-represent the amount of data in a partition before though. It is a minor, trivial issue and nothing to worry about. I doubt if your symptoms indicate any problem at all.

If the symptoms don't go away by themselves after a reboot,  start with the simplest things first, like emptying your trash. Then try doing 'sudo apt-get clean' and see if that helps. ```
sudo apt-get clean
``` if that doesn't do it, then maybe a filesystem check will fix it. The easiest way I know to do that would be to boot Ubuntu and enter the command 'sudo touch /forcefsck' and then reboot.```
sudo touch /forcefsck
``` Or you can edit /etc/default/rcS to have, ```
FSCKFIX=yes
```During the rebooting, if you watch it,  you should see some white text appear on a black monitor background and a progress bar will show your file system being checked. The trouble is, I'm not sure if that will check you seperate /home. It might only check your /

We can also issue the fsck or e2fsck and other useful commands from a Live CD, such as Dapper Desktop, Knoppix or GParted LiveCD,  I don't know very much about filesystem checking and repairing that way, but I'm trying to find out more. There are several unanswered threads here in Ubuntu forums on the subject, so maybe it needs some further investigation. I'm sure there are people around who know but maybe they can't be everywhere at once.  Here's the man page for it if that helps. [e2fsck]("http://www.linuxcommand.org/man_pages/e2fsck8.html")
Here's what the Wikipedia has to say,[B][http://en.wikipedia.org/wiki/Fsck](http://en.wikipedia.org/wiki/Fsck)

[/B]If you want to be using the most up to date and modern version of GParted, like I do, then the best thing to do is to download the latest [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php"). It is best to burn it to a CD-RW disk instead of a plain CD, because a better version will be out again sometime soon, and you will want to update it then. GParted LiveCD has had full 'move' support for all filesystems since issue 0.3-1 as well, which was released on the 4th of September, and has already been superceded by 0.3.1-1.
Gparted has improved a lot since it was first added to the Ubuntu LiveCD version, and so has it's integration with Ubuntu's installer. A newer version of Gparted has been coming out around every two or three weeks.  The LTS issue of Dapper Drake already has a much improved GParted than the original Dapper Desktop CD had.  I imagine the next version of Ubuntu, "Edgy Eft", when that is released, will probably feature an even newer version of GParted than Dapper Drake has now too. 

Regards, Herman :D

---

