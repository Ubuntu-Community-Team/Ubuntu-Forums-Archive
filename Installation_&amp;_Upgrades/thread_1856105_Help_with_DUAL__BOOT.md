---
title: "Help with DUAL  BOOT"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by Waffelafelus on 2011-10-07
Hi I'm completely new to this forum and I haven't even started using Ubuntu  yet but I would like to start as soon as possible.
Long story short I tried to dual boot Ubuntu with windows 7 and it didn't  work. I partitioned my hard drive, I restarted with my usb inside (my usb is  installed with Ubuntu), the Ubuntu start up stuff came up, i typed in my  information and it loaded everything. The last thing I had to do was restart the  computer and from there it was supposed to boot into windows 7 but I got the error  code: 0xc0000225. I looked around and couldn't get any solid info. After  thinking about it, I think my problem is that when I partitioned my hard drive  something went wrong. 
 
According to the disk management section of my computer there are 4  partitions already installed. ( I have an HP Pavilion dv6 quad edition)
 
C
HP_Tools
Recovery D
System
 
I have a 1tb hard drive so I took 300 GB from C: so there was 300 GB of  unallocated space.
Then I made the unallocated space into drive U: for Ubuntu but before I  finished it said that it was going to turn my drives from basic to dynamic disks  and that I wouldn't be able to boot from them or something like that. I didn't  think much of it at the time so I pressed "OK" and it turned all my drives from  the color blue to the color green. And, instead of blue equaling primary  partition, it made it into green equaling normal or something like that.
next I restarted my computer and made it boot from my usb.
Ubuntu started up and I chose to do "Something Else" where I configured it  with
a: / (root), /boot, /swap and /home partitions.
 
I finished up normally after that and when I was asked to restart that's when  I got the error code: 0xc0000225
 
If anyone can help I would greatly appreciate it. My best guess is that when  I originally partitioned it WASN'T supposed to turn green but I'm not sure how  to fix that. I've read that I can only have up to 4 primary partitions but the  computer already comes with those installed and I don't want to delete any  because I don't know what they're for.
 
Hope someone can help.

---

### Post by xtjacob on 2011-10-07
Try running startup repair, then reinstall grub. The startup repair should be on one of the recovery partitions which you can boot up onto from the boot menu. Instructions for reinstalling grub can be found here: [http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05](http://maketecheasier.com/restore-grub-2-as-the-main-bootloader/2010/05/05)

---

### Post by oldfred on 2011-10-08
Welcome to the forums.

Dynamic disks are a huge problem, some Windows tools do not work with it. Do not create partitions with Windows, just use Windows to shrink the main c: partition. Delete any partitions just created that do not have data you want to save. Best to have good backups. Windows official policy is total backup, erase drive,  and recreate basic partitions. 

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.

The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529).

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

