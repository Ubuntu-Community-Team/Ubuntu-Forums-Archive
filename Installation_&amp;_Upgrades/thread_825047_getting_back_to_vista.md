---
title: "getting back to vista"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by drewsfca on 2008-06-10
I installed ibuntu today and may have incorrectly done so.  I can't figure out how to get back to vista.  I thought I had selected the partition option to have both running.  Is there a way to verify if vista is still on my laptop?  Rebooting gives me no option.

---

### Post by ajgreeny on 2008-06-10
Boot to the live ubuntu CD and run System>>Administration>>Partition manager.  This will show you with a GUI what partitions are on your machine.  Hopefully there will be one at the start of the disk which is NTFS, ie Vista.  It will probably be noted as sda1, but it will depend on the setup of your hard disk;  manufacturers often add a system partition at the beginning with restore info on it.  If you are confused, come back again with gparted's  findings.

---

### Post by jrharvey on 2008-06-10
You dont even have to do that. Boot into ubuntu and go to your computer and if you see a drive other than "file system" then it may be your windows drive. There is a possibility you may have selected the wrong install method. IDK because I always select manual partition.

---

### Post by Pumalite on 2008-06-10
If Vista is there; you can boot it with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
If it doesn't boot right away; try to fix the MBR first.

---

### Post by Rallg on 2008-06-10
EDIT: The others (above) and I were writing at the same time. So, I removed what I wrote here, since the above advice is likely to produce results faster.

---

### Post by drewsfca on 2008-06-10
Gracias.  The only other item there is CD-RW/DVD Drive.  So, I'm guessing vista is gone?  I have a backup disk though so all is not lost.  Just time, humility,  and a few files not on my external drive.

---

