---
title: "Windows Installation Question"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by jorgecarrillo150990 on 2008-02-29
Well, I am planning to get again to dual-boot with Windows since I know I need it (gamer),  so what do you think is better?
1. To repartition Gutsy and install windows, reconfigure GRUB, etc...
2. Wipe out Ubuntu (make backup), install Windows and again install Ubuntu.

If you recommend me choose number 2: Is there a way to backup "everything" from themes, programs, wallpapers, programs, engines, and again, PROGRAMS?
Thanks in Advance

---

### Post by dstew on 2008-02-29
I don't think you can backup everything without cloning the partition. You can do that. There is a program called clonezilla that might work.

I think if you partition, and leave room at the front of the drive, WIndows will go in there. Maybe you will have to format the partition FAT32 so Windows recognizes it as a partition. Then, WIndows will probably go in there, and leave your other partitions alone (I would hope!) It will no doubt replace grub with its own boot loader, but that is easy to fix. I don't think Windows will delete your ext3 partitions, but it might.

---

### Post by Pumalite on 2008-02-29
Backup everything:
[http://restore.holonyx.com/](http://restore.holonyx.com/)
[http://ubuntuforums.org/showthread.php?t=564836](http://ubuntuforums.org/showthread.php?t=564836)
[http://users.bigpond.net.au/hermanzone/p13.htm](http://users.bigpond.net.au/hermanzone/p13.htm)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html](http://web2linux.blogspot.com/2007/11/apples-time-machine-now-for-linux.html)
you could try sbackup - in the repos
DAR
[http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html](http://www.ubuntugeek.com/disk-archive-backup-and-restore-using-dar-and-kdardar-frontend.html)
[http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)
[http://clonezilla.sourceforge.net/clonezilla-live/](http://clonezilla.sourceforge.net/clonezilla-live/)
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it
Delete everything in yout hard drive. Make 2 new partition. The first, dedicated to Windows, formatted ntfs, the 2nd for Ubuntu, format it ext3 if you want. Then install Ubuntu, go Manual and choose the partition you made. Give 10 GB for '/'
1 GB for /swap
The rest for home
Then press 'Forward'

---

