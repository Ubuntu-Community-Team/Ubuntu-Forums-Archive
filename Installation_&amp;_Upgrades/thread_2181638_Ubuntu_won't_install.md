---
title: "Ubuntu won't install"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by Dan_Hayes on 2013-10-18
OK, im sure this is something simple(i Hope), but when i try to install Ubuntu form cd, it comes up and says
ubiquity components. partman failed with exit code 2
from this point, it starts the installation back from the beginning
I had to get a new hard drive for this machine and it does not have an operating system on it,
please HELP!!!

---

### Post by Bashing-om on 2013-10-18
Dan_Hayes; Hello, Welcome to the forum.

Is ubuntu to be the only operating system installed ? Are Windows, UEFI, ISRT, raid meta data a factor, how are you formatting (GPT ??)the hard drives ?

For starters, show us what we are working with.
From the liveDVD - try ubuntu mode - ; Post the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```
This will answer a lot of questions, and prompt for others.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Dan_Hayes on 2013-10-19
Here is what it says/ oh and this will be the only operating system installed.

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Error opening /dev/sda: No medium found                            
Retry/Cancel? sudo parted /dev/sdb unit s print

---

### Post by Bashing-om on 2013-10-19
Dan_Hayes; Hey,

From that last I gather there is no partition tables (no formats) on the hard drive. Thus, there is nothing to detect.
What I would do; fire up GParted from the liveDVD and format that drive to accommodate the operating system I am to install . 
If only ubuntu is to be installed, put some thought into how I want the hard disk partitioned and why. 
There are pros and cons to any partitioning scheme. I personally prefer separate "/", /home, /swap and /var. But that is for the way I use and monitor my system. You may want it simple and direct as the whole drive formatted ext4 and a single partition to house the entire operating system.

I hope I am not confusing you. Before you can impose a file system, the hard disk has to be formatted to accommodate that file system. There is nothing wrong - at this stage -  in experimenting with GParted, learning and wiping out what you have done .. and doing a re-do. 

In any event, format that hard drive as file type "ext4" and if a "smaller" drive use partitioning scheme "msdos" - msdos DOES NOT equal MicroSoft Disk Operating System, in this instance - >  for ubuntu.

The help files in GParted are difficult to comprehend until you have some experience with the utility .. but the instruction is complete and totally doable.
-and- if at first you do not succeed, use the utility to wipe the hard drive (delete all partitions) and start all over once more. The installer will honor any partitions you make with GParted .. It is likely though that you will have to re-confirm if you do separate partitions which partition is to be used for "/" --- (/ means "root", the top directory for the ubuntu file system) in the installer. 

There is no luck to this .. all prior prudent planning and learning how to implement the plan.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by siepo on 2013-10-19
> **Dan_Hayes said:**
> Here is what it says/ oh and this will be the only operating system installed.

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ sudo parted -l
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Error: Error opening /dev/sda: No medium found                            
Retry/Cancel? 
This rather sounds like it does not find the harddisk at all. Did you check your cables?
> sudo parted /dev/sdb unit s print
What output did you get here? The same?

---

### Post by Dan_Hayes on 2013-10-19
WOW, ok sounds a little over whelming, but I'm up to the challenge in the morning. Thank You for all of the positive direction, i will keep you up to date on my progress, and a sincere thank you

---

### Post by Dan_Hayes on 2013-10-20
Yes i did check and re-check everything and it still is not recognized

---

### Post by Bashing-om on 2013-10-20
Dan_Hayes; Well,

In order for anything to be recognized one must have that device formatted for a some file system.
Fire up the liveDVD, boot to the desk top, top of the launcher is the "dash" -> search term "GParted" -> icon below the search box, click on the GParted icon to activate.
Post back a screen shot of GParted's screen. I expect that the disk will show as "unallocated" space.

[INDENT]we will see what is to be seen
[/INDENT]

---

### Post by Dan_Hayes on 2013-10-20
Yes it just shows no devices detected

---

### Post by Dan_Hayes on 2013-10-20
The Hard Drive is a WD5000AAKX if this makes a difference

---

### Post by Bashing-om on 2013-10-20
Dan_Hayes; Hey,
Same drive(s) as I am using on this system.
As you say it is a brand new hard disk, it will have to be formatted before a file system can be installed onto it.

Show us a screen shot of GParted from that liveDVD, and I will try and guide you to format that drive, to the best of my poor memory. I have formatted disks numerous times.. I do not even think about what I am doing so my direction may not be exact - seek confirmation from the help file.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Dan_Hayes on 2013-10-20
Well, there is no screen shot, when i open gparted, it brings up gparted, searches for a drive, and that's it. it doesn't show a thing and says no drives detected on the bottom of the screen. I also took out the live CD and rebooted into bios, not detected there either.

---

### Post by Bashing-om on 2013-10-20
Dan_Hayes; very un good !

Ok back up, regroup and once more check your wiring ..is this a sata or an ide drive ?
Make sure you have the separate power cable connected if it is sata;
ide drive:
Double check the ribbon connectors and insure how the cable select mode is pinned- at the back of the hard drive -  if this is a ide drive.
Single hard drive ? set the pinning to master;
other drives on the same ribbon ? set the mode to slave if there is a hard drive connected on this cable before the hard drive you want to boot from.
if CD/DVD drive is on that same ribbon, try setting the pinnning as "cable select".

If bios does not see that drive, you are indeed ---dead in the water ---!

Else you are looking at breaking out a voltage meter and a logic probe to see what is not going on.

[INDENT][INDENT]but, where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Dan_Hayes on 2013-10-22
Well, when the computer re-boots, i can hear the drive clicking then thats it, going to get a new hard drive, will keep you up to date. Thanks for all of your help so far

---

### Post by Bashing-om on 2013-10-22
Dan_Hayes; Hey,

Yep, that is the next logical thing to try. If you have a known good drive lying about, would be a good idea to stick it in and see what happens. At least rule out bios problems.

Lord willing, I will

[INDENT][INDENT]still be here in the event of need
[/INDENT][/INDENT]

---

