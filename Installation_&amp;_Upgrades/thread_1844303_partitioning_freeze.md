---
title: "partitioning freeze"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by pndragon on 2011-09-14
I accidentally wiped my linux drive and was forced to install.

the problem is that none of the iso's i've downloaded (alternate or live) can get past the partitioning stage---they all freeze at 33%. What can I do?

---

### Post by Hakunka-Matata on 2011-09-14
Hi, 
Can you boot into a liveCD?, choose the 'try without installing" choice.
And What Release are you using?

---

### Post by pndragon on 2011-09-15
> **Hakunka-Matata said:**
> Hi, 
Can you boot into a liveCD?, choose the 'try without installing" choice.
And What Release are you using?

booting into the livecd is not a problem. i have tried every release since 9.04

---

### Post by Hakunka-Matata on 2011-09-15
Good, please post output of 
```
sudo sfdisk -luS
sudo fdisk -lu

```

---

### Post by pndragon on 2011-09-15
for:
```
sudo sfdisk -luS
```
output:
```
sudo: unable to execute /sbin/sfdisk: Input/output error
```
for:
```
sudo fdisk -lu

```
output:
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xce6c9356

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b2a98

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   191195135    95596544   83  Linux
/dev/sdb2       191197182   195371007     2086913    5  Extended
/dev/sdb5       191197184   195371007     2086912   82  Linux swap / Solaris

```

This is after getting the kubuntu 11.10 beta alternative cd to succeed during partitioning but fail during the software install. it succeeded with a grub install. when trying to download missing software, keeps asking for "sudo dpkg --configure -a" but this does not fix probs

:(

---

### Post by pndragon on 2011-09-15
Before I forget to mention it, the previous information was obtained and posted with the ubuntu 10.04lts livecd

---

### Post by Hakunka-Matata on 2011-09-15
what I would do with your machine is try to boot to Ubuntu LiveCD.  

[LIST]
[*] And choose to just 'try Ubuntu without installing' or however it's listed this time around
[*]then look at your disk partitioning, is it ok?  Which partition are you going to tell the installer to install your *what version?* of Linux into.
[LIST]
[*]*do I have to tell you these things?  I don't want to offend, but I have no idea how familiar you are with the command line*.
[*]```
sudo sfdisk -luS
```
[*]```
sudo gparted
```
[/LIST]
[*]what are you trying to achieve, what's the goal?
[/LIST]

---

### Post by srs5694 on 2011-09-16
If it's freezing during the partitioning stage, my first guess is that it's not technically the partitioning that's failing (that involves writing just a few sectors to the disk), but the associated filesystem creation (which involves writing much more data to the disk). One possibility is that the system is encountering a disk problem. There are at least three things you can do to help clarify this matter:


[list]
[*]Take a screen shot of the screen when the system freezes in the Ubuntu installer and post it here. This may include some clue about what's going on that you've overlooked but that somebody here will recognize. (Use a digital camera if you can't find a way to take a screen shot in software. I know it's possible in software, but I don't recall the exact procedure myself -- I think I might have run the installer after booting in the "try it now" mode and launched a separate screen-shot program to do this in the past, but my memory is a bit foggy.)
[*]Run a [SMART](http://en.wikipedia.org/wiki/S.M.A.R.T.) utility to obtain diagnostic information on your hard disk. If it's physically failing, this has a good chance of providing you with clues about the problem. In Linux, SMART utilities include the text-mode smartctl and GUI tools such as gsmartcontrol and the SMART options in Palimpsest Disk Utility. Disk manufacturers also often have SMART tools available that run under Windows. Unfortunately, SMART results can be difficult to interpret, so you may need to post details here to figure out what's going on.
[*]Use the text-mode filesystem creation tools, such as mkfs, in a Terminal window. For the output you posted, you'd type "sudo mkfs -t ext4 /dev/sdb1" to create an ext4 filesystem on /dev/sdb1 -- but verify with another fdisk run that the partitions haven't changed! (Sometimes disks change identity between boots.) Typing the text-mode command in this way is more likely to produce useful diagnostic information about any problems that might turn up. If it succeeds, you could run the installer again and tell it to *not* create a new filesystem on the root (/) partition; however, if this works it would leave the question of why it failed. Perhaps there's some problem that would crop up again in the future.
[/list]


I recommend starting with posting the screen shot and/or running a SMART utility, simply because if you're not familiar with tools like mkfs, a typo could cause you to damage other data on your disk.

---

### Post by pndragon on 2011-09-16
output of smartctl:
```

Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST3100011A
Serial Number:    4LH0GYAH
Firmware Version: 3.02
User Capacity:    100,030,242,816 bytes [100 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Fri Sep 16 19:41:20 2011 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(  430) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  58) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   050   046   006    Pre-fail  Always       -       96080210
  3 Spin_Up_Time            0x0003   098   098   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       406
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   070   060   030    Pre-fail  Always       -       11446491
  9 Power_On_Hours          0x0032   065   065   000    Old_age   Always       -       31517
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       458
194 Temperature_Celsius     0x0022   045   056   000    Old_age   Always       -       45
195 Hardware_ECC_Recovered  0x001a   050   046   000    Old_age   Always       -       96080210
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 14 (device log contains only the most recent five errors)
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 14 occurred at disk power-on lifetime: 5069 hours (211 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 10 8e 86 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00868e10 = 8818192

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 f1 8d 86 e0 00      05:40:58.126  READ DMA EXT
  25 00 20 f1 8d 86 e0 00      05:40:58.114  READ DMA EXT
  10 00 ff 00 00 00 e0 00      05:40:58.105  RECALIBRATE [OBS-4]
  25 00 20 f1 8d 86 e0 00      05:40:58.089  READ DMA EXT
  25 00 20 f1 8d 86 e0 00      05:40:58.089  READ DMA EXT

Error 13 occurred at disk power-on lifetime: 5069 hours (211 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 10 8e 86 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00868e10 = 8818192

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 f1 8d 86 e0 00      05:40:58.126  READ DMA EXT
  10 00 ff 00 00 00 e0 00      05:40:58.114  RECALIBRATE [OBS-4]
  25 00 20 f1 8d 86 e0 00      05:40:58.105  READ DMA EXT
  25 00 20 f1 8d 86 e0 00      05:40:58.089  READ DMA EXT
  25 00 08 51 fd 8b e0 00      05:40:58.089  READ DMA EXT

Error 12 occurred at disk power-on lifetime: 5069 hours (211 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 10 8e 86 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00868e10 = 8818192

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 f1 8d 86 e0 00      05:40:58.126  READ DMA EXT
  25 00 20 f1 8d 86 e0 00      05:40:58.114  READ DMA EXT
  25 00 08 51 fd 8b e0 00      05:40:58.105  READ DMA EXT
  25 00 08 a9 bb 8c e0 00      05:40:58.089  READ DMA EXT
  25 00 08 a1 bb 8c e0 00      05:40:58.089  READ DMA EXT

Error 11 occurred at disk power-on lifetime: 5069 hours (211 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 10 8e 86 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00868e10 = 8818192

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 20 f1 8d 86 e0 00      05:40:58.126  READ DMA EXT
  25 00 08 51 fd 8b e0 00      05:40:58.114  READ DMA EXT
  25 00 08 a9 bb 8c e0 00      05:40:58.105  READ DMA EXT
  25 00 08 a1 bb 8c e0 00      05:40:58.089  READ DMA EXT
  25 00 08 f1 fa 5c e0 00      05:40:58.089  READ DMA EXT

Error 10 occurred at disk power-on lifetime: 5069 hours (211 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 01 60 fb d1 e0  Error: ICRC, ABRT 1 sectors at LBA = 0x00d1fb60 = 13761376

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 59 fb d1 e0 00      05:40:47.020  READ DMA EXT
  25 00 08 59 fb d1 e0 00      05:40:37.362  READ DMA EXT
  25 00 08 e9 ba 8c e0 00      05:40:37.362  READ DMA EXT
  25 00 08 81 7a 8c e0 00      05:40:37.362  READ DMA EXT
  25 00 10 a9 46 d2 e0 00      05:40:27.873  READ DMA EXT

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

Doesn't look good does it? I guess I need a new drive.

---

### Post by srs5694 on 2011-09-16
You've got a Seagate drive, many of which are known to produce ridiculously high values for some of the error items in SMART tests, even when they're fine. My vague understanding of this is that they encode some other data in the high bits, which produces those huge numbers and makes them hard to interpret. Thus, I wouldn't chuck the drive out the window just yet. Somebody with more experience at interpreting Seagate SMART results may post, or you can try one of Seagate's own utilities and see what it says.

On the positive side, smartctl has reported a "PASSED" status. That's not always a guarantee that all is OK, but it might be.

SMART says the disk has recorded 14 ATA errors, but the latest of these occurred at the drive's lifetime-on hour count of 5069, whereas it's now at 31517 -- in other words, those problems aren't even remotely recent, so they aren't a symptom of a current problem. It could be there was some sort of glitch that's now been corrected.

So, based on *my* knowledge, I'd call the SMART results inconclusive; however, *my* knowledge of SMART data is only moderate. Somebody with more SMART know-how might be able to say something more definitive.

---

### Post by pndragon on 2011-09-17
Most of this thread has been posted from a different machine...

I've never gotten the kubuntu desktop to run---all that I ever saw from it was a blank screen. ubuntu, xubuntu, lxde had a massive number of system errors.

I finally managed to get window maker to open and even opened firefox for awhile... the previous post came from there.

an update to xorg threw a lot of segmentation defaults and dpkg errors and window maker crashed. now i don't know how to clear the dpkg errors.

---

### Post by srs5694 on 2011-09-17
> **pndragon said:**
> Most of this thread has been posted from a different machine...

I've never gotten the kubuntu desktop to run---all that I ever saw from it was a blank screen. ubuntu, xubuntu, lxde had a massive number of system errors.

I finally managed to get window maker to open and even opened firefox for awhile... the previous post came from there.

an update to xorg threw a lot of segmentation defaults and dpkg errors and window maker crashed. now i don't know how to clear the dpkg errors.

If you're saying that you installed KDE on a standard Ubuntu installation and had problems, that's peculiar. Although I seldom use KDE as a whole, I've got it installed on one of my Ubuntu systems (a standard 32-bit Ubuntu 11.04 setup), and it works fine for me.

It's not clear what "dpkg errors" you've got. If you're having problems with that, I recommend you start a new thread with a relevant title and whatever details seem relevant, such as cut-and-pasted dpkg error messages.

---

### Post by pndragon on 2011-09-17
I've been using some variation of ubuntu since 5.10... I am a confirmed convert from and have been for a few years. This is just the first time that I've had any really major problems during an install.

At this point, I am no longer sure exactly what is going on. I will say that I have learned more about the inner workings of my command-line in the last few days than I had in the previous few years. Not necessarily a bad thing. I just may be forced to look at replacing this hunk of junk... something that I really can't afford at this time.

By the way, I finally got the kubuntu desktop to come up. It's not quite as buggy as ubuntu. I begin to think that unity is a mistake...

---

### Post by mörgæs on 2011-09-18
So, is the problem solved?

---

### Post by pndragon on 2011-09-18
> So, is the problem solved? Not completely. Currently I am using fluxbox, but as of today I can get the kubuntu desktop to load without starting a chain of catastrophic system failures. On the other hand, firefox in kde keeps crashing and is virtually unusable.

At one point today, I was getting a segmentation fault error and a core dump every time I tried to use synaptic or aptitude.

It is very possibly a hardware problem and I will be looking into that as soon as I can. There is also a good likelihood that it is a software problem because I am after all trying to install a beta release.

I just don't know

---

### Post by MAFoElffen on 2011-09-18
> **srs5694 said:**
> You've got a Seagate drive, many of which are known to produce ridiculously high values for some of the error items in SMART tests, even when they're fine. 

So, based on *my* knowledge, I'd call the SMART results inconclusive; however, *my* knowledge of SMART data is only moderate. Somebody with more SMART know-how might be able to say something more definitive.
+1 

I volunteer for a Non-Profit Computer Recycler, where one of the things we do is to disassemble, test, reassemble computers and give new life to them as Linus Machines.  We sell used parts... We also repair computers.  We have to guarantee/warrantee this equipment, so we do test all this used equipment extensively!  Everything that doesn't pass muster is "recycled."

Seagate drives?  Yes, they historically show a lot of errors.  Even other company's drives, even though they test out with bad SMART results, doesn't definitively mean the drive is "bad".  We have to look at the other test results and sometimes we just use another "test suite" to test it with.  Seagate drives somehow seem to "show" more errors in some of these test suites.

SMART data and it's implementation is not really as standardized as people think between different companies...  So a SMART Test sometimes has problems consistently reading that data from drive to other drive.  Using Seagate's "Seamonkey" would be what to test that drive from.  Some particular Seagate drives also seem to have weird quirks as the first drive in Linux and Unix implemented RAID array's, (just changing the order corrects that) but that is another subject.

---

