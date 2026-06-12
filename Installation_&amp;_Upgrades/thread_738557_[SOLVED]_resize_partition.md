---
title: "[SOLVED] resize partition"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by upthelum on 2008-03-28
I recently set up ubuntu dual boot with xp pro, the laptop came with xp. I used partition magic to shrink the C drive to make space for ubuntu, which is fine and all is well, runs fine, graphics are fine. Because everything is going so well i would like to shrink the winblows C drive again and re-allocate the space to ubuntu as i'm running out of space and want to try and make a full shift to linux. Can i do this from xp with no problems as i read one or two posts that sounded contradictory to each other about the operation so i'd like to confirm this will go hassle free.

Thanks...

---

### Post by upthelum on 2008-03-28
bump

---

### Post by phidia on 2008-03-28
I think you want to use something like partition magic to shrink the window partition is that correct? 
That should work but anyone who has adjusted a partition and lost it will tell you to back up what you don't want to lose. Partition size changing is invasive surgery.
It's a good idea to make note of all your partitions-do an fdisk -l (from the ubuntu install) and print out the results. Hope that helps.

---

### Post by upthelum on 2008-03-28
I know partition magic hasn't been kind to me in the past. How do i back up linux, shrinking xp is fine it's re-sizing ubuntu i'm concerned about?

---

### Post by Pumalite on 2008-03-28
I prefer Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
It will take hours either way and you DEFINITELY have to backup first.

---

### Post by metalf8801 on 2008-03-28
check out systemrescue which has partitioning software on it 

[http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)

oh and remember to back up first no matter what tools you use

---

### Post by darkenergy on 2008-03-28
i'd also recommend a (not too old) live cd/dvd with gparted (eg ubuntu 7.10 or 8.04, live)

had never problems this way (where as i once lost more than one partition using partition magic.

---

### Post by ZALMAN on 2008-03-29
On my second installation of ubuntu I did not leave enough disk space for everthing I wanted to load, so I used partion magic within xp, Everthing seemed fine until reboot, Grub would not load properly or even recover. I subsequently reformated that partition and reinstalled ubuntu. The partitioning software in windows works fine for winx but not for linux. I would suggest using a linux partition manager.

---

### Post by upthelum on 2008-03-29
> **Pumalite said:**
> I prefer Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
It will take hours either way and you DEFINITELY have to backup first.

Ok i downloaded and burned gparted i'll have a go tonight. What's the best way to backup ubuntu?

---

### Post by Pumalite on 2008-03-29
Take your pick:
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

---

### Post by upthelum on 2008-03-29
> **Pumalite said:**
> Take your pick:
[http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan](http://users.bigpond.net.au/hermanzone/p13.htm#overall_plan)
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

I have a question about this link [http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)

Backup:

tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

And Restore:

tar xvpfz backup.tgz -C /

My question, the / after --exclude=/sys, is this the beginning of the path to where i want the backup file located?

---

### Post by Pumalite on 2008-03-29
Nope. That command forms a file in your hard drive than you can then backup to an external drive:

'My exact testing steps:
1. Freshly Installed 7.10 (Gusty-Gibbon-i386-desktop) on a Laptop.
2. Copied test data to system (600MB / 1,400 files) to both my home dir and desktop. And then installed KTron application (just a small-game to test if it works later).
3. Opened the Terminal and ran the following:
Code:

cd /
sudo tar cvpzf backup.tgz --exclude=/etc/fstab --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /

4. I then inserted a USB flash-drive & backed up the 'backup.tgz' and removed the drive.'

---

### Post by upthelum on 2008-03-29
Ok i got the file. I tried to write the backup file straight to media/Hitachi_hdd but it wrote to / so at least i know it works. 

Thanks all.

---

### Post by upthelum on 2008-03-30
All went well re-sizing ubuntu drive but it took quite some time. I started gparted last night about 10pm and it was still finishing at 8.30 this morning, could this be related to the screensaver? Also it forced a chkdsk when i booted winblows to check it was ok which is fine. So i now have 15gb more to play with, thanks to all...

= happy bunny :smile:

---

### Post by Pumalite on 2008-03-30
It takes a long time because there are a bunch of files to move. It's normal.

---

