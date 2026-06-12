---
title: "Dual boot win 8 machine with unbutu 12.04 grub works but cant boot ubuntu"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by sunwukong2 on 2014-02-13
Im running an old acer PC with a 1 TB Hd.  Win 8 was installed and I set it up for Ubuntu 12.04 using a live CD.  It worked fine then one day it just would not boot.  I tried several things to fix, changed swap file (actually added a swap file) reinstalled grub2 via boot repair still no joy.

boot repair log file is at  [http://paste.ubuntu.com/6926309/](http://paste.ubuntu.com/6926309/)  

I am about a raw amature with linux and also very new to win 8, having used win xp pro for several years.

Any suggestions to repair would be helpfull.  Lacking a repair option it would be nice if I could recover my emails and bookmarks for thunderbird and firefox (I think I can find the files)

VR
Sunwukong

---

### Post by Bucky Ball on 2014-02-13
From your Boot Repair info:

```
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   195,751,175   195,751,113   7 NTFS / exFAT / HPFS
**/dev/sda2         987,146,240 1,953,521,663**   966,375,424   7 NTFS / exFAT / HPFS
/dev/sda3         195,751,934   987,146,239   791,394,306   5 Extended
/dev/sda5         195,751,936   974,565,375   778,813,440  83 Linux
/dev/sda6         974,567,424   987,146,239    12,578,816  82 Linux swap / Solaris
```

... and this warning further down:

```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```

... is a problem, but maybe not what is causing this. 

Notice how sda2, which I have marked in bold, starts and finishes with number higher than the next partitions?

---

### Post by oldfred on 2014-02-13
You have the old XP partition alignment where it starts on sector 63. But new 4K drives really need new alignment you drive will be very slow. But that is not related to boot issue.

But Boot issue may be an old BIOS and very new large hard drive. Some old BIOS do not support booting from beyond 137GB. And it may work and then an update writes a boot file further into drive and it stops working.
You need to verify if BIOS sees drive correctly & can boot from beyond 137GB.

Also did you turn off fast boot or always on hibernation in Windows. That does not work with dual booting.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

    
Grub will only boot working Windows so you may need Windows repairs.

       Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

   First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by sunwukong2 on 2014-02-14
Thanks to Bucky Ball and Old Fred, (funny my Mom called me Old Pat, I guess because I was her oldest).  Unfortunatly for me it is like asking where is the bathroom and getting an answer like the Andromeda Galaxy is heading this way at xxx bazillion mph so the bathroom location will be changing on a cosmic scale,  now the real question is just how bad do you need a bathroom right now!

I do really appreciate the help.  I remember when the internet was a lot more friendly, helpfull and open but those days are long gone.  But amazingly there are still folks who are so helpfull and willing to share.

Windows 8 says I'm OK not optimal but OK,  It reports no problems with my HD or system or bios.  I get a nice clean looking Grub menu but only Windows is working.  From the Grub menu I can see
 
hd0=unk file system
hd0,msdos6 = unk file system
hd0, msdos5 = grb boot and ubuntu
hd0,msods2 = my D partition (in windows where my data is stored)
hd0,msdos1 = my windows C partition where my program files are set up

At this point I guess I would like to simply copy off my thunderbird e-mail and address book and my mozilla firefox favorites (from the ubuntu partition) and move it to say a USB thumb drive.  

From the grub menu I can ls -la the Home directory and find the .Thunderbird folder (but I can't make a copy)

If I boot from the live CD I can use the Ubuntu graphic interface and move to / show the .Thunderbird folder but again I can not make a copy.

I guess if I can copy my data off then I can Delete the Ubuntu Partitions,  Back up Windows 8.  Re partition Windows 8 and reinstall Windows 8 (if this is possible).  Most of my documents and saved materials are safe in the other windows partition (D:) so I feel safe there (perhaps that is an illusion).

Then the next step would be to realign the partitions to optimize dual booting and Ubuntu and Windows.  I like the speed of windows 8 and ubuntu and the fact that I can do some precision astrophotography and spectral analysis but windows 8 completely broke my connection to my weather station, and oscilloscope (both running thru db9 connectors to serial ports).  I see that I can use windows system restore from an image to just start all over.  I hope this works.

---

### Post by oldfred on 2014-02-14
If you move NTFS partitions you will need to run chkdsk. Best to have a Windows repair flash drive as it may not boot after move.
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

I regularly copy entire thunderbird & Firefox profiles to laptop when travelling & back. But I have mine in a shared NTFS data partition from when still using XP. I have not copied to my shared Linux formatted partition.
You may be into permission & ownership issues. You can try sudo from live installer. Just do not move system files around as administrator you have capability to also damage system. Use gksudo for graphical apps.
gksudo nautilus

---

