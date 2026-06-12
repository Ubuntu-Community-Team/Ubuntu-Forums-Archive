---
title: "Ubuntu wrongly recognizes partitions, can't install"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by thacursedpie on 2011-06-10
Hi all!

I want to install ubuntu on my laptop, but I'm running into some issues.

The laptop came with Windows 7 pre-installed and I wish to keep it because some software needed for my study only runs on Windows (as well as some games :P).

Using a Windows I shrunk one of my partitions and made a new one in the remaining space (done with Windows 7's standard partition program, not a third party program). I needed to format the new partition, therefore it's filesystem is NTFS. (Besides this new partition I have two other NTFS partitions containing the Windows installation and some of my files, respectively).

Windows recognized the new partition so I thought I was ready to go. I popped in my Ubuntu live-cd (on an usb, if that's important), started the installation. But when the screen to select the install-partition came up, it showed the wrong partitions. To be more precise, it showed the correct number of partitions, but they all had wrong sizes! Also, the installation was not able to tell me how much space was already used in each partition, which seemed odd to me.

I'm not going to install ubuntu yet, because I am afraid my data will be overwritten (though I have backups, it's just such a hassle to re-install Windows).

Does anyone have an idea what can be done about this?

I have already looked around on the internet and found the following thread:
[http://ubuntuforums.org/showthread.php?t=886985&page=2](http://ubuntuforums.org/showthread.php?t=886985&page=2)

The issue seems very similar to mine. It states that adding "all_generic_ide" to the end of the bootline has fixed the issue for some people. Being new to Linux (you might have noticed other posts by me about Linux, that was me helping my dad :P) I have no idea where this "bootline" is situated... Searching around on the internet returned some info, but it all only seems relevant for versions of Ubuntu which have already been installed.

Any help would be greatly appreciated!

PS:
GParted is able to show some partitions. The partitioncount seems correct, but the sizes are all off! I'm sure I don't have a 992.50 kB partition. It displays a symbol and clicking on that gives the info that GParted needs additional packages for NTFS support. Perhaps this is why the sizes are wrongly recognized? 
How could I even add a package to a live cd?

PS2:
I am able to browse my Windows partitions using the Ubuntu live cd. It shows all files correctly. Odd...

---

### Post by oldfred on 2011-06-10
Did you create a 5th partition as you can only have 4 partitions in MBR/msdos partitioning that windows just about has to have. If so then windows converted to dynamic? You should have a message. Dynamic is not compatible with anything.

Post this from the liveCD so we can see what is where.

```
sudo fdisk -lu
```

---

### Post by thacursedpie on 2011-06-10
Yes, I think it was the fifth partition... I didn't know there would be anything special with creating a fifth partition. :( Windows did pop up with a message, I think it indeed said the new partition would be dynamic, but I'm not sure. 

I think the log will be more of more help to you. sudo fdisk -lu gives:
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x91a29a16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            2048    20973567    10485760   27  Unknown
/dev/sda3   *    20973568    21178367      102400   27  Unknown
/dev/sda4        21178368   594534399   286678016   42  SFS

Disk /dev/sdb: 3953 MB, 3953131520 bytes
2 heads, 63 sectors/track, 61277 cylinders, total 7720960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0070fc22

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          64     7720959     3860448    b  W95 FAT32


EDIT:
I did some more research and I found the following:
- Windows only supports up to four "primary partitions". If you want more (like I did), you need to convert the disk containing the partitions from "basic" to "dynamic". Windows did this automatically. It did pop up with a warning but silly me thought only the new partition would be dynamic, not the whole disk. Why I can still boot into Windows is beyond me..!
- OS's can only be installed on basic partitions.
- converting from dynamic to basic partitions is hard ([http://thelazyadmin.com/blogs/thelazyadmin/archive/2007/01/17/Converting-Dynamic-Disks-Back-to-Basic-Disks.aspx](http://thelazyadmin.com/blogs/thelazyadmin/archive/2007/01/17/Converting-Dynamic-Disks-Back-to-Basic-Disks.aspx))

According to the Windows partition program thing I have 5 partitions at the moment:
0: 10.00GB (recovery partition, primary)
1: 100MB   (recovery partition, active, primary)
2: 273.40GB(NTFS, Windows OS install, dynamic)
3: 152.97GB(NTFS, my data, dynamic)
4: 29.30GB (NTFS, empty, dynamic)

This puts me in a bit of a difficult situation. I want to somehow install Ubuntu, but I think that's going to be difficult, because I don't have room for another "primary" partition. Perhaps I could get rid of one of the recovery partitions... But I'm not sure if those play a role for Windows (considering one was listed as "active").

I'm going to sleep on it for a bit, I don't want to act too quickly (then again, worst that can happen is I have to reformat my drive. That's just a lot of hassle).

Hints and tips are still very much appreciated :).

---

### Post by oldfred on 2011-06-10
I would first delete the empty partition. Part of the advantage of dynamic or Logical Volume Management (LVM) in Linux is that physical partitions are not a limit. One logical can be from two or more physical partitions even across drives. But it adds a level of complication and if one drive dies, the logical partition is broken and you best have good backups.

The windows LVM/dynamic is similar in how it works, but if your logical to physical is still the same and you only have 4 partitions you may be able to recover to basic partitions with third party tools. Windows only says backup, reformat, and reinstall. You still should have good backups.

Always best to use windows tools for windows (shrinking windows partitions etc) and Linux tools for Linux(creating new partitions etc).

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Have not done any of this and some have reported that one method or the other works.
Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by thacursedpie on 2011-06-11
Wow! Thanks for all the info!

I'll be sure to check out all the links and decide on my next move. I'll report back with results (if I succeed or not...).

Again: thanks!

---

### Post by thacursedpie on 2011-06-18
Okay, a quick update.

I backed up my data to make sure I wouldn't lose anything.

Today I deleted one of my partitions (formerly my D partition). I expanded my Windows partition (called C).

My drive was still dynamic though, so I downloaded MiniTool Partition Wizard Professional 6.0. I tasked it to revert my drive from dynamic back to basic - it needed a restart to perform the job.

After the drive had been altered the computer restarted... And was asking for a boot device. Not good, obviously. MiniTool's promise of a conversion from dynamic to a basic drive without data loss seemed sketchy at this point.

Luckily I had a Windows 7 DVD ready, which I inserted and I started the installation process, thinking I'd lost all my data (though I had backed it up, it's of course a hassle to put it back on my computer :P).

Upon installation I was presented with a screen listing all current partitions. Lo and behold: my old partitions were still there, and it even correctly listed the sizes of the partitions. Noticing this I thought I might not be screwed altogether. I pressed 'back' on the installation wizard and I noticed there was an option to 'repair an existing install'. hm...

I started the repair, clicked 'fix startup problems - in case Windows is not able to start up'. In the next screen it was supposed to list my partitions, but the screen was empty. I ignored this and pressed 'next' anyway.

It started the repairs (which took quite a while, perhaps 15 - 20 minutes). Afterwards it told me I should reboot my computer.

I rebooted and... I was able to boot into Windows! Success!

So at this point I am ready to install Ubuntu. Will report back with results.

Update:
Success!
I created an extended partition in the free space (approx. 50 GB). In this extended partition I created:
Logical partition, 20GB, root (/)
Logical partition, 3GB, swap
Logical partition, remaining space, /home

And started the installation. Everything went smoothly :).

I restarted the computer and on boot it gives a nice menu where you can choose the OS. Windows still works :) and all my data is still intact. Only downside: Windows 7 seems soooo slow now :S

---

### Post by Quackers on 2011-06-18
Excellent result! Well done :-)
And handy for the rest of us to know too!

---

### Post by thacursedpie on 2011-06-19
Thanks :). I really enjoy ubuntu so far. I'd switch over completely if most of my games and necessary applications were supported... But that's a catch-22 of course :S.

IMO this thread can be locked, not really anything to add anymore.

---

