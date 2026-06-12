---
title: "Why does 14.04 partition go read-only after running for a week?"
date: 2014-07-27
forum: Installation &amp; Upgrades
---

### Post by John Chambers on 2014-07-27
I did lots of searching, found lots of "my new install can't see/write its root partition" messages, but none with this problem, which I'm seeing on two different machines with xubuntu 14/04.

What happens is that the installation seems to work, boots up, and I have lots of fun (;-) installing and configuring stuff.  Then after about a week or so, when I'm not actually doing anything on it and the machine is basically idle, suddenly everything starts to fail.  My ssh sessions from other machines simply disconnect.  I can ssh back in, but then I see the same things I see on the machines' screens:  

: ls -la /tmp/.X11-unix
ls: reading directory /tmp/.X11-unix: Input/output error
total 0
:

These failures seem quite random.  /tmp itself and a few other subdirs are readable, but some subdirs are not.  Similarly, some files in a directory are readable, while others get Input/output errores.  Right at this moment/ "tail -48f /var/log/kern.log" gets an Input/output error, but "tail -47f /var/log/kern.log" works fine.

The first time this happened, I thought I'd screwed things up, and did a new install.  It seemed to work, but it's now about a week later, and a few hours ago it started getting these errors.

Sometimes I get other errors. For example, "df ." gets "Segmentation fault", while "file /bin/df" gets "Input/output error".   And probably the most significant:

: touch /tmp/foo
touch: cannot touch ‘/tmp/foo’: Read-only file system
:

Tests in other directories show that I can't write or touch any file anywhere.  So the entire partition is apparently read-only.

In the first install, when this happened and I tried to reboot (perhaps so that an fsck would be done), I found that it simply didn't boot at all.  So I tried the xubuntu install disk, and couldn't find any tools there that would diagnose the problem.  

But that's a different question, which I'll start researching again as soon as I post this.  If it's fixable without a reboot, or there are tools that can diagnose and repair the problem, I'd like to try those first.

---

### Post by Bashing-om on 2014-07-27
John Chambers; Oh Boy,

From the description given, I would highly suspect hard drive failure.
What does the SMART reveal ?
```

sudo apt-get install smartmontools

``` ( if it is not already installed)
Then run the test:
```

sudo smartctl --all /dev/sdX

``` where sda[color=red]X[/color] the 'X' is the hard drive identifier as in sda and/or sdb, sdc.

If "disk utility" is installed there is the GUI means to do that assessment.

[INDENT][INDENT]don't look good for the home team,
[INDENT][INDENT][INDENT][INDENT][INDENT][INDENT]yet
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2014-07-27
I agree with Bashing-om's suggestion. Hard drive failure or corruption is a frequent cause of that kind of problem.
It can come from a drive nearing it's end (hooray for backups!), or -once- from a poorly behaved second OS that corrupted a bunch of (what it considered) unused space.

My 14.04 installs have been solid. After weeks of hard use, mine *don't* go read-only.

---

### Post by John Chambers on 2014-07-27
Funny thing, the system became a total zombie, so I rebooted it --- and it came back up with no problems.  So I did the suggested install, and ran:

: smartctl --all /dev/sdc
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.11
Device Model:     ST3500320AS
Serial Number:    9QM3G5B8
LU WWN Device Id: 5 000c50 00cc60683
Firmware Version: SD15
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Sun Jul 27 22:42:09 2014 EDT

==> WARNING: There are known problems with these drives,
THIS DRIVE MAY OR MAY NOT BE AFFECTED,
see the following web pages for details:
[http://knowledge.seagate.com/articles/en_US/FAQ/207931en](http://knowledge.seagate.com/articles/en_US/FAQ/207931en)
[http://knowledge.seagate.com/articles/en_US/FAQ/207951en](http://knowledge.seagate.com/articles/en_US/FAQ/207951en)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632758](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=632758)

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
data collection: 		(  634) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 ( 117) minutes.
Conveyance self-test routine
recommended polling time: 	 (   2) minutes.
SCT capabilities: 	       (0x103b)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   109   093   006    Pre-fail  Always       -       21586483
  3 Spin_Up_Time            0x0003   096   094   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       65
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       73484366
  9 Power_On_Hours          0x0032   040   040   000    Old_age   Always       -       53229
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       64
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       196611
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   069   056   045    Old_age   Always       -       31 (Min/Max 31/31)
194 Temperature_Celsius     0x0022   031   044   000    Old_age   Always       -       31 (0 20 0 0 0)
195 Hardware_ECC_Recovered  0x001a   048   027   000    Old_age   Always       -       21586483
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

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

:
-----------
I really don't know how to interpret much of this.  I gave it /dev/sdc because "df ." gave me info for /dev/sdc7.  Some of the above looks like error reports, but it also says things like "PASSED" and "No errors".  So is it failing?  If so, how would I know?  Maybe I should google the docs for this tool, and see if I can make sense of it.

---

### Post by SeijiSensei on 2014-07-28
There must be another hard drive in there as well, right?  /dev/sda?

---

### Post by John Chambers on 2014-07-28
Yes, the machine actually contains 4 disk drives.  But I was planning to ask some separate questions about that.  The software on the xubuntu install disk refuses to show the others, and I haven't yet found any way to fix this.  On both of the machines I've tried it on so far, its menu of places to install has had exactly one entry, and nothing I can find shows me the others.  Also, the partitions are tiny.  On this machine, all 4 disks are 500 GB, but df says the single partition (sdc7 for some reason) is 117803 "1M-blocks".  My first install attempt actually used sdc5, and said it was about twice that size, but I can't see sdc5 any more; "df -a" only sees /dev/sdc7, and that was the only choice that the install CD allowed.  It have no idea who created sdc7, which didn't used to be there.  I did see a question asking whether I wanted to revise the partitions, but I didn't (knowingly) give it permission to do that.

The previous ubuntu install (the only OS on the machine) had a disk utility program that showed all 4 disks, and all their partitions, so I knew what names it used, and could do things like unmount them, run fsck, etc.  But all that seems to have been taken away, and it's not obvious what if anything has replaced it.

I've been reading a lot of ubuntu install guides online, and a pattern seems to be emerging, that they all just give examples with little explanation, and never mention the possibility that something might go wrong.  In my experience, troubleshooting software is always needed during installs.  I suspect that such software exists on xubuntu, but I haven't been able to discover what it might be called, and none of the names I know seem to exist. (I'm considering of going back to knoppix, which emphasizes diagnostic tools, and give up on ubuntu, until I know what all the tools are for 14.4. ;-)

In any case, this all seemed to take second place to the question of why the system was shooting itself in the foot by making the file system read-only, ensuring that error messages would no longer be written to log files.  (I did have several windows showing tail-f on various /var/log files, and they all simply stopped when this happened.  This did give me the time of the failure, but blocked everything else, since most programs just said "Input/output error" and exited.  It was curious that tail -f continued to mostly work, as I showed above, but of course that gave little further information.)

---

### Post by Bashing-om on 2014-07-28
John Chambers; Hey,

Let's see what we can do to straighten up the situation. ( an install only requires the 5 P's ( Prior Prudent Planning Preventing Pi** Poor Performance)) The install process is fairly straight forward - once you have done it a time or 3 .

So, show us what we are working with:
From a liveDVD(USB), so no partitions are in use/mounted ->
Post back the outputs - Between code tags, please please - of terminal commands:
```

sudo blkid
sudo fdisk -lu
sudo parted -l
lsblk -f

``` and let's see if we can determine what is driving the system nuts.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Looking for the real booting partition on which hard drive containing the 'root' file system
.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by John Chambers on 2014-08-05
Well, I've sorta been bogged down, and also managed to lose the info on how to get back to this page, but I finally found it again.  One question I've been unable to find an answer for:  The above commands produce a LOT of output, and there's no chance I could copy it by hand to this window.  All I've been able to do is get the output displayed on a screen.  Is there some good way to get it out of the install CD's display and over to a message here?  The machine comes up with no usable network info (so the widespread advice to install or upgrade various packages is useless).  I thought it'd be easy to just plug in a USB memory stick and copy it there, but that failed, mostly because I don't seem to see it after it's plugged in.  There's gotta be a faster way that (attempting to) copy it by hand from the screen ...

The machine does have 4 500-GB drives installed as 2 RAID1 drives, and I remember that the old system's disk utility did show them and said that they were fine.  The above list of commands only shows 3 disks, with only dev/sdc7 showing in the mount or df -a tables.  (And the CD drive, of course).

---

### Post by Bashing-om on 2014-08-05
John Chambers: Welcome back ;

Raid throws a whole new light on the situation. The desk top releases do not have the tools installed to deal with raid.
see:
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/461470)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Basically:
install the raid tools
```

sudo apt-gt install dmraid

```
dmraid signatures, which can be listed via :
```

sudo dmraid -r -c

```

And if you so choose to remove the raid meta data from the drive(s);
```

sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
sudo dmraid -E -r /dev/sdc
sudo dmraid -E -r /dev/sdd

```
Do check that the drive nomenclatures remain a constant, these designations can and do change.
The UUID's are a constant.
To keep in mind what drive is what the following commands will be helpful:
```

sudo blkid
sudo fdisk -lu

```

-----------------------
Maybe, when the raid situation is under control, udev will be under control -> and the usb thumb drive will then be recognized .
Else, in the interim, we can try and mount that usb thumb drive from the terminal.

[INDENT][INDENT]see, there is cause and
[INDENT][INDENT][INDENT][INDENT][INDENT]effect
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

