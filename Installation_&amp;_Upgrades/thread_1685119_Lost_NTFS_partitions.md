---
title: "Lost NTFS partitions"
date: 2011-02-10
forum: Installation &amp; Upgrades
---

### Post by bee19 on 2011-02-10
Hello everybody. I need very urgently your help. Yesterday I was insatalling ubuntu to girlfriends laptop where was installed Vista before. And shes hdd looked like this - 
 
C: - 80GB - NTFS - Installed Vista - primary partition
D: - cca 280GB - NTFS - her files - logical partition
Another hidden partition where was HP backup/restore with vista - NTFS - primary partition
 
So I deleted first partition in Acronis disk director and then started install ubuntu 10.10. But......... When I installed ubuntu these partition LOST and Im very unlucky and i dont have any backup. I dont know what happend because i did it a lot of times before and during installation a chose first option (i dont know how it calls someting with "use free space") not used entire disk nor manually edit. But all partitions and data are LOST :((((
 
Now the disk looks like this (Im not sure if it is 
 
dev/sda/
dev/sda1/ - ext3 where is ubuntu now - more then 360GB
dev/sda2/ - swap - 3,5GB
 
So question is. Is there any way to repaire it? With any SW in any operation system? Is there any way to recover whole partitions? Or only files? Or nothing? :( During install when i chose where install ubuntu it didnt take a long time (just few seconds) so disk wasnt formated (nor low level formated) so i am convinced that files are still there. 
 
So what can i do? Try some software? Some linux software or commercial as diskinternals or someting else? I tried Acronis Disk Director to find partition but there is of course nothing if ther is whole disk as ext3+swap and no free space. So Could I try to delete these partitions (ext3+swap) and then try to find partitions? Or it will find only last partition extt3+swap?
 
Many thanks for any advice...
 
BG

---

### Post by bee19 on 2011-02-10
Main question... Could I delete these currents two partitions and then try to recover partition? The partition what i would like to recover beginns in 80gb so it could be untouched... But can I delete these currents? And than create new ntfs or let it unalocated and try testdisk? could it recover whole partition? Or i cant recover partition anymore?

---

### Post by SivaCoHan on 2011-02-10
I think you may need someone professional . Just find if there is any company can rescovery your data from you hdd

---

### Post by Grenage on 2011-02-10
> **bee19 said:**
> Main question... Could I delete these currents two partitions and then try to recover partition? The partition what i would like to recover beginns in 80gb so it could be untouched... But can I delete these currents? And than create new ntfs or let it unalocated and try testdisk? could it recover whole partition? Or i cant recover partition anymore?

You can try and recover the data using destdisk, but if you're still using the computer at the moment - stop.  Don't boot from the drive, and certainly don't write anything to it.

---

### Post by P4man on 2011-02-10
You could try with testdisk, but boy, are you in trouble. Dont create any new partitions, dont even boot the machine from the hdd, boot from a rescue cd and see if you can get anything off.

BTW, too late now, but AFAIK ubuntu 10.10 no longer has the option to install in unpartitioned space. They removed that option for some reason.

---

### Post by oldfred on 2011-02-10
IF the install went into the area that was the partition you really wanted to delete then you may be able to recover the other parition, but installs often write to various areas of the drive.

More info on testdisk. If testdisk does not bring back partition then you can use photorec. Photorec scans drive for data that looks like files. It recovers much data but not files names.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html]("http://members.iinet.net.au/%7Eherman546/p21.html")
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

