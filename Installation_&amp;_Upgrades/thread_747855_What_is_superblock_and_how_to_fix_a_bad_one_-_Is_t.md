---
title: "What is superblock and how to fix a bad one - Is this related to SATA?"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2008-04-07
I am unable to boot a new installation of Ubuntu.
I have installed the Alternate version as well as the Live version. I have installed them as 63 bit as well as 32 bit. 

It always the same. I install and when I reboot I get to the splash screen and the text box where you enter the user name only consists of a verticles line under the left hand edge of the graphic text "UBUNTU".

I then run Gnome Partition Manager and I see a "!" on the hda partition and the "information" on the partition states "Can not mount partition. Bad superblock"

If I boot using recovery mode the resulting text continues to flash across the screen for a couple 
seconds and then stops. The last few lines are this... 


27.280869 Idm_validate-partition-table(): Disk read failed. 
27.280731 Dev hda: Unable to read RDA block 0. 
27.280934 Unable to read partition table. 
27.281094 Sr 0:0:0:0: Attached scsi generic sg0 type 5. 
Done. 


After a few minutes the following appeared. 


Check root=bootarg cat /proc /cmdline or missing. 
Modules, devices: cat /proc /modules ls /dev. 
ALERT! /dev /disk /by-uuid/2cf89e46-7499-4575-95cb-6d6e85bb9472 does 
not exist. 
Dropped to a shell. 


A couple times I got errors that referred to SATA. Which made me wonder, could my new SATA dvd drive be causing this?
Could it be a be hard drive? Could it be BIOS settings?

This problem occurs with a lone Ubuntu installation. It occurs when dual booted with Windows. When install next to windows the errors are on both the Ubuntu and Windows partitions. When I only install Windows alone everything is fine and the partition shows no errors.


I have reinstalled Ubuntu MANY MANY times and never had trouble with it. I have downloaded new copies of it so I know it is not a bad dvd or download. I have tried the Alternate version, the Live version and I have tried Gutsy and Hardy, so I know it is not the version that is causing the problem.

Come on guys. I've posted umteen times on this problem in differant places and no one will touch it. What the hell is a superblock and what makes it go bad?

It is not a computer problem since windows runs fine alone. It is not a Ubuntu glitch since all versions do it. 

Help!!!!!!!

---

### Post by tamoneya on 2008-04-07
a superblock is part of the filesystem and therefore has nothing to do with sata vs ide.  This basically means that part of your filesystem has been corrupted.  You should use file system check utility(fsck)
```
fsck -p /dev/sda1
```
take a look at the man pages [http://www.hmug.org/man/8/fsck.php](http://www.hmug.org/man/8/fsck.php) if you want more details about fsck and superblocks.

note: fsck should only be performed on file systems that are NOT mounted.  In other words: use the live cd

---

### Post by sofasurfer on 2008-04-07
But I reformated over and over. Why would the file system be corrupted. Doesn't a reformat recreated the file system?

I can not enter commands as you suggest since I can not get past the boot screen.
What third party software can I use to repair whatever is damaged?
At this time I have windows installed by itself. Is there anything I can do through windows?

Thanks for you help. Please don't go away. Well, you can go to bed but don't forget to check back tomorrow.

---

### Post by sofasurfer on 2008-04-07
I think I may have just found an answer. Tell me if this sounds good.

Tomorrow I will reinstall Ubuntu. When it freezes up on boot again I will verify that I have the "bad superblock" error agaiin and then I will repair the superblock by inserting my Ubuntu "live" cd and this will give me access to a comand line where I will repair the superblock by following the directions on this web site...

[http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html](http://www.brunolinux.com/04-The_File_System/Damaged_Superblock.html)

---

