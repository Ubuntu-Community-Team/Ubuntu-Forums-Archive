---
title: "A Hard Disk is reporting health problems I am desperated"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-06-21
I begin to experience this message"Disk utility: A Hard Disk is reporting health problems", I have reinstalled ubuntu11.04, that hasn't helped.
I am using dual-booting with windows 7, windows does not have the hard disk problems.

---

### Post by nomko on 2011-06-21
Try installing smartmontools, you can find it in synaptic.
In a terminal venster: [COLOR=black]**sudo **[FONT=Verdana]**smartctl -s on -a /dev/*** > smartmontools.txt** ,*** = mounting point of hard disc, i.e.: sda1 or sda2 this can be found with the command [FONT=Verdana][COLOR=black]**ls /dev/sd***[/COLOR][/FONT][/FONT][/COLOR]. The last part of the command (> smartmontools.txt) is a text file created by smartmontools which shows the status of every hard disc. Post the output the disc who's got the health poblems.

---

### Post by Grenage on 2011-06-21
> **hoboy said:**
> I begin to experience this message"Disk utility: A Hard Disk is reporting health problems", I have reinstalled ubuntu11.04, that hasn't helped.
I am using dual-booting with windows 7, windows does not have the hard disk problems.

Does Windows 7 check SMART data?  Either way, while it could be a false alarm, I'd really recommend backing up any important data.

---

### Post by sammiev on 2011-06-21
Follow the instructions above for safety. I have had the same problem as you now for a year. Window reports all is well, well linux reports the error you have and still does. I am running will no issues. GL :)

---

### Post by hoboy on 2011-06-21
> **nomko said:**
> Try installing smartmontools, you can find it in synaptic.
In a terminal venster: [COLOR=black]**sudo **[FONT=Verdana]**smartctl -s on -a /dev/*** > smartmontools.txt** ,*** = mounting point of hard disc, i.e.: sda1 or sda2 this can be found with the command [FONT=Verdana][COLOR=black]**ls /dev/sd***[/COLOR][/FONT][/FONT][/COLOR]. The last part of the command (> smartmontools.txt) is a text file created by smartmontools which shows the status of every hard disc. Post the output the disc who's got the health poblems.
when I use lucas@lucas:~$ ls /dev/sd*.
ls: cannot access /dev/sd*.: No such file or directory

---

### Post by nomko on 2011-06-21
> **hoboy said:**
> when I use lucas@lucas:~$ ls /dev/sd*.
ls: cannot access /dev/sd*.: No such file or directory
 
Try hd instead of sd. What do you get then?

---

### Post by hoboy on 2011-06-21
> **nomko said:**
> Try hd instead of sd. What do you get then?

the same
ls: cannot access /dev/hd*.: No such file or directory

> **hoboy said:**
> the same
ls: cannot access /dev/hd*.: No such file or directory

I don't know if this means anything at all.
 ls /dev/ sd*.
ls: cannot access sd*.: No such file or directory
/dev/:
autofs           loop4               ram6      stderr  tty34  tty63      ttyS5
block            loop5               ram7      stdin   tty35  tty7       ttyS6
bsg              loop6               ram8      stdout  tty36  tty8       ttyS7
btrfs-control    loop7               ram9      tty     tty37  tty9       ttyS8
bus              mapper              random    tty0    tty38  ttyprintk  ttyS9
cdrom            mcelog              rfkill    tty1    tty39  ttyS0      uinput
cdrw             mem                 root      tty10   tty4   ttyS1      urandom
char             net                 rtc       tty11   tty40  ttyS10     usb
console          network_latency     rtc0      tty12   tty41  ttyS11     usbmon0
core             network_throughput  scd0      tty13   tty42  ttyS12     usbmon1
cpu              null                sda       tty14   tty43  ttyS13     usbmon2
cpu_dma_latency  nvidia0             sda1      tty15   tty44  ttyS14     vcs
disk             nvidiactl           sda2      tty16   tty45  ttyS15     vcs1
dvd              oldmem              sda3      tty17   tty46  ttyS16     vcs2
dvdrw            pktcdvd             sda4      tty18   tty47  ttyS17     vcs3
ecryptfs         port                sda5      tty19   tty48  ttyS18     vcs4
fb0              ppp                 sda6      tty2    tty49  ttyS19     vcs5
fd               psaux               sda7      tty20   tty5   ttyS2      vcs6
full             ptmx                sdb       tty21   tty50  ttyS20     vcsa
fuse             pts                 sdc       tty22   tty51  ttyS21     vcsa1
fw0              ram0                sdd       tty23   tty52  ttyS22     vcsa2
hidraw0          ram1                sde       tty24   tty53  ttyS23     vcsa3
hidraw1          ram10               sg0       tty25   tty54  ttyS24     vcsa4
hidraw2          ram11               sg1       tty26   tty55  ttyS25     vcsa5
hpet             ram12               sg2       tty27   tty56  ttyS26     vcsa6
input            ram13               sg3       tty28   tty57  ttyS27     vga_arbiter
kmsg             ram14               sg4       tty29   tty58  ttyS28     zero
log              ram15               sg5       tty3    tty59  ttyS29
loop0            ram2                shm       tty30   tty6   ttyS3
loop1            ram3                snapshot  tty31   tty60  ttyS30
loop2            ram4                snd       tty32   tty61  ttyS31
loop3            ram5                sr0       tty33   tty62  ttyS4

---

### Post by mikewhatever on 2011-06-21
You should try and figure out what's wrong with the HDD, as 'health problems' is a rather vague term. In the Disk Utility, select your HDD and click the 'SMART Data' button, scroll through the entries looking for the ones marked in red. Post a screenshot.

If you want to use smartmontools, as suggested above, run the following commands in a terminal:
```
sudo apt-get install smartmontools

sudo smartctl -s on -a /dev/sda > ~/Desktop/smartmontools.txt
```

The last command will create a text file on your desktop, attach it to the next post.

---

### Post by dFlyer on 2011-06-21
> **hoboy said:**
> I begin to experience this message"Disk utility: A Hard Disk is reporting health problems", I have reinstalled ubuntu11.04, that hasn't helped.
I am using dual-booting with windows 7, windows does not have the hard disk problems.

My advice is to backup everything you want to keep. If your drive is starting to fail the sooner you do it the better. If it's bad sectors you might want to think about replacing it ASAP. Windows is more tolerant of bad sectors than linux.

---

### Post by hoboy on 2011-06-21
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Blue Serial ATA family
Device Model:     WDC WD6400AAKS-07A7B0
Serial Number:    WD-WMASY5431844
Firmware Version: 01.03B01
User Capacity:    640,135,028,736 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jun 21 18:35:54 2011 CEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF ENABLE/DISABLE COMMANDS SECTION ===
SMART Enabled.

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  73)	The previous self-test completed having
					a test element that failed and the test
					element that failed is not known.
Total time to complete Offline 
data collection: 		 (11160) seconds.
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
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 131) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   165   159   021    Pre-fail  Always       -       4725
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1846
  5 Reallocated_Sector_Ct   0x0033   122   122   140    Pre-fail  Always   FAILING_NOW 621
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5277
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1812
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       191
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1846
194 Temperature_Celsius     0x0022   110   101   000    Old_age   Always       -       37
196 Reallocated_Event_Count 0x0032   094   094   000    Old_age   Always       -       106
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: unknown failure    90%      5277         -
# 2  Conveyance offline  Completed: unknown failure    90%      5276         -

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

---

### Post by mikewhatever on 2011-06-21
The errors definitely don't look good. Better be safe then sorry, so backup your files and look for a new HDD.

---

### Post by psusi on 2011-06-21
The drive is toast; get your data off of it and replace it asap.

---

### Post by hoboy on 2011-06-23
ok my last solution is I am going to buy a new stationary computer.
what is the best mark is the best ?
Compaq, hp ? what else ?
what is the best processor ?

---

### Post by psusi on 2011-06-23
I don't buy OEM computers, but if I did, it would be from Dell.  Stay away from comcrap and HP.

---

### Post by sammiev on 2011-06-23
> **psusi said:**
> I don't buy OEM computers, but if I did, it would be from Dell.  Stay away from comcrap and HP.

+1 and totally agree! but I would not buy dell either. GL :)

---

### Post by rpaskudniak on 2011-07-04
> **mikewhatever said:**
> You should try and figure out what's wrong with the HDD, as 'health problems' is a rather vague term. In the Disk Utility, select your HDD and click the 'SMART Data' button, scroll through the entries looking for the ones marked in red. Post a screenshot.

If you want to use smartmontools, as suggested above, run the following commands in a terminal:
```
sudo apt-get install smartmontools

sudo smartctl -s on -a /dev/sda > ~/Desktop/smartmontools.txt
```

The last command will create a text file on your desktop, attach it to the next post.
Er, Mikewhatever,

First, thanks for posting the tidbit about the Smartdata button, which I did not notice from the tool when it was opened by the [Examine] button.

I found this thread while searching for a solution to the same problem.  We all know this is a vague term.  It is the system that is being vague about both what kind of health problem and which disk is is that experiencing [un]said health problem.

For the benefit of othere users: Start the Disk Utility this way from the Ubuntu classic/gnome menu):
Systen -> Administration -> Disk Utility.

Indeed, I have found it reporting that my Western Digital 320KB drive is in imminent failure, with a high read-error rate and 43 bad sectors.  Exactly what to do is another issue - I think a fsck now is in order Whatever, I'd better back it up ASAP!  But from Windows; the good stuff is in NTFS.

Unfortunately, the Smart Data tool will not run the self-test, which would make things somewhat easier.

Bottom line: Use that Disk Utility as your starting point.  Where to go from there, I'd also like some help!

Thanks.

---

### Post by PartisanEntity on 2011-07-06
Interesting enough my external USB Lacie drive has started reporting Disk Failure Imminent since two days. I am in the process of backing up right now.

The disk is relatively new, so my gut feeling tells me Ubuntu may be the issue. But making a backup nonetheless.

Will try to analyze the problem once the backup is done.

---

### Post by switcha on 2011-12-10
Hi folks,
Any news/updates on a resolution to this issue? I recently had the same issue with my wd elements 640 gig hd. Though, I originally encrypted the file system using the option that Disk Utility permits.
After doing this, I was locked out of my hd I couldn't access my data using the supplied password. It finally worked and I transferred my data. Since then, I have formatted it several times and the SMART Data self-tests fail.
Its weird because I have 157 sectors that are Current Pending Sector Count.
When I format it using xp disk management it appears healthy.
I have a feeling this issue has arisen from the disk utility encryption. See attachment for my smartmontools.txt output.

---

