---
title: "Install of 14.04 hanging"
date: 2015-02-11
forum: Installation &amp; Upgrades
---

### Post by jamescc1968 on 2015-02-11
I am fairly new to Ubuntu.  I have had 13.01 on this computer for about 6 months with no problems.  I love it.  It was put on by a friend who did a complete wipe of windows per my request. (it was running very slowly and he said files were corrupt. (I assume he was talking about the files, not microsoft.)  ;) Anyway, I was updating/ upgrading files and I could have rebooted or something while this was going on and it would not reboot.  It went into a screen to follow certain things...I did all of those to no avail.I had all of my files backed up so I decided to do a complete install of 14.01.  I followed the directions ...made a live boot disk and a live USB.  Both of them will run ok but when I try to just install It hangs or I get the installation crashed. it is as follows:
Error copying files
[Errno30] read-only file system : '/target / mnt'

when I did a check disk from the Ubuntu software it said "2 files bad"  may be a bad disk...needs to be in a cooler area....
and when it trys to report it says "problem cannot be reported"

When I first had the problem I took it to a computer repair place and they checked the HD and they said it checked out to be fine.
I did a check disk to find it was ok too.

The computer is a Toshiba satellite L655  I am running Ubuntu 14.04 from the Live USB right now
memory 3.7 GiB
intel pentium(R) CPU P6100 @2.0 GHz x 2
Graphics card intel Ironlake Mobile
OS 64bit
Disk 2.0 GB
I think the hard drive is 300GB

Please help.

James

*******It does not actually say hard drive error....I tried to edit the title...it wont let me.  It says the install has crashed and then what is typed above.

---

### Post by efflandt on 2015-02-12
Sounds like the drive may be failing. How did you test it? A partition automatically being remounted read-only is a sign of drive issues. Linux does that to try to protect remaining data.

Seagate has SeaTools for DOS which can boot from CD to test a drive [http://www.seagate.com/support/downloads/seatools/](http://www.seagate.com/support/downloads/seatools/)
Similarly Western Digital has their Data Lifeguard for DOS which can boot from USB memory [http://support.wdc.com/product/download.asp?groupid=613&sid=2&lang=en](http://support.wdc.com/product/download.asp?groupid=613&sid=2&lang=en)

The Linux partition at the far end of my desktop hard drive began failing as I got into Linux Steam early 2013 and filled my too small partition with games. The first symptom was when I would suddenly not have permission to write to my own home directory because the drive had remounted read-only. Fortunately I have a small backup Linux system on SSD where I could fsck my hard drive Linux, eventually with options to lock out badblocks. That got me by for awhile. But as it got worse I finally replaced the drive about a year ago.

Drives automatically transparently remap good sectors in place of bad sectors regardless of OS. But if all the error sites are used up and you start seeing bad sectors (or have read/write issues) it can only get worse.

---

### Post by mörgæs on 2015-02-12
Changed the thread title.
Are you able to read SMART data from a live boot?

---

### Post by jamescc1968 on 2015-02-12
A pro checked it out..im not sure what they use..ill ask him tomorrow...  I will try your advice too.  

Thanks

---

### Post by jamescc1968 on 2015-02-12
what is SMART data?

---

### Post by jamescc1968 on 2015-02-12
I used the seagate sea tools.  SMART data was enabled and not tripped.  it passed a short test and failec a long one.  The computer company which tested it said I should reformat the disk and try to install Ubuntu again....  should I do this...and what do you recomend I use to do the reformating/partitioning the drive.  I have not preferences at all...it can be very general.

---

### Post by mörgæs on 2015-02-13
Formatting the drive is done automatically during the install so you don't need a special tool for that. Just select 'use enire drive for Ubuntu'.

If you install again I suggest 14.10 for comparison.

---

### Post by jamescc1968 on 2015-02-13
I ran the DISKS software in Ubuntu and the disk showed good with 2100+ bad sectors. I assume is this is bad enough to warrant a new drive.

---

### Post by jamescc1968 on 2015-02-13
Thanks for your help...im trying to close this thread or say "solved"  still looking.

---

