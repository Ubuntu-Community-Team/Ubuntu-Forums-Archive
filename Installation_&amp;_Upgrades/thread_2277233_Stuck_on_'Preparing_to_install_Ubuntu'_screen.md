---
title: "Stuck on 'Preparing to install Ubuntu' screen"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by martin159 on 2015-05-07
I've been trying to install Ubuntu for almost two hours with no success. The installer is stuck on 'Preparing to install Ubuntu' screen. I don't know what to do next.

Specs:

FX8350
GTX770
16GB RAM

---

### Post by Bucky Ball on 2015-05-07
*Thread moved to **Installation & Upgrades**.*

Might have better luck here.

[LIST]
[*]Prior to installing did you try Ubuntu running from the live media?
[*]Did you check the live media for defects (there is an option on the first option screen when you boot from the disk to 'Try Ubuntu', 'Install Ubuntu', etc.)?
[*]Where did you download the ISO, which release and how did you burn the image to the install media?
[/LIST]

---

### Post by martin159 on 2015-05-07
[LIST]
[*]Prior to installing did you try Ubuntu running from the live media? **Yes, I did.**
[*]Did you check the live media for defects (there is an option on the first option screen when you boot from the disk to 'Try Ubuntu', 'Install Ubuntu', etc.)? **I did not check it for defects, I first tried to install Ubuntu and I got stuck, then I tried 'Try Ubuntu' but I got stuck again.**
[*]Where did you download the ISO, which release and how did you burn the image to the install media? **I downloaded the ISO from Ubuntu website, it's the latest release. I used Rufus and Universal USB installer. First, I used Universal, and then I used Rufus with a different thumb drive.**
[/LIST]

---

### Post by Bucky Ball on 2015-05-07
> **martin159 said:**
> [LIST]
[*]Prior to installing did you try Ubuntu running from the live media? **Yes, I did.**
[*]Did you check the live media for defects (there is an option on the first option screen when you boot from the disk to 'Try Ubuntu', 'Install Ubuntu', etc.)? **I did not check it for defects, I first tried to install Ubuntu and I got stuck, then I tried 'Try Ubuntu' but I got stuck again.**
[*]Where did you download the ISO, which release and how did you burn the image to the install media? **I downloaded the ISO from Ubuntu website, it's the latest release. I used Rufus and Universal USB installer. First, I used Universal, and then I used Rufus with a different thumb drive.**
[/LIST]

Yes, you did try Ubuntu from the live media? So it didn't work then and you went ahead and install? Bit confused as you go on to say you tried to install and got stuck, then you went for the option 'Try Ubuntu' and you got stuck. So you've always gotten stuck on 'Try Ubuntu'? Do you get stuck when you choose 'Check for defects'?

If you can't get to a desktop via 'Try Ubuntu' then something's not right. When you're at that option screen, could you try hitting F6 and choosing 'nomodeset' then proceeding?

---

### Post by martin159 on 2015-05-07
Here's what I do:

Click on the 'Try Ubuntu'
Ubuntu boots up
I click on 'Install Ubuntu' icon
Installation starts
I put a password to my WiFi
Next step is to pick if I want to install 3rd party software, I ticked the box and clicked continue. The installer is stuck

Also, no errors were found.

---

### Post by martin159 on 2015-05-07
Here's the screenshot: [http://imgur.com/KEb1bK9](http://imgur.com/KEb1bK9)

---

### Post by Bucky Ball on 2015-05-07
Don't tick the third-party repos box and see how it goes. Easy peasy to do that later. If that doesn't work, try not ticking 'Install updates' and see if that makes a difference. Just wondering if, even though it says the internet is working, maybe it is seeing the router fine but not the WAN. 

Also, hit F6 at the selection screen and go with the nomodeset option. You can try these suggestions one at a time or in combination and see if something works ...

---

### Post by joe_schmo2 on 2015-06-11
Looks like this is a common problem with a variety of resolutions, none of which have worked for me.  I am trying to dual boot Windows 7 and Linux 14.04, on my Acer Aspire using a USB stick.  I have posted a question in askubuntu but no help there, I'm getting ready to give up but thought I would try my luck here. 

My install "hangs" on Preparing to install, but things are actually happening, just not sure what to make of them.

I boot using USB, then I select "Install Ubuntu" from the options, 10 minutes later I am brought to a desktop and I double click on the Install Ubuntu file.  I get to the Preparing to Install part, I select <ctrl><alt> F1 which brings me to a terminal window.  The following are things I've noticed poking around as the install proceeds (never past "Preparing to Install", maybe this is all useless information, I hope not but I'll add it here in hopes it sparks some thoughts from a helpful reader.

-  20 minutes into the install I see the partman process start and a log file created in /var/log.
-  30 minutes into the install I see a new directory created /sys/btrfs
- 40 minutes into the install I see some files created in the directory talked about above.
- 50 minutes into the install I see the partman.log file written to again.
- 60 minutes into the install I see files and directories written to /sys/module/xfs
- 75 minutes partman.log file written to again (looks like it sees my partition), no errors
- 77 minutes auth.log file written to as follows:
      -  "session opened for user root (uid=0)
      -  "session closed for user root (uid=0)
- 90 minutes, I give up.

Any ideas?  

Thanks in advance

---

### Post by oldfred on 2015-06-11
It takes me 10 minutes to install to pre-partitioned drive installing from hard drive to SSD. So something wrong.
Often if you have file corruption on any partition the partitioner takes forever to time out. Check that chkdsk not needed on any NTFS partitions or that they are not hibernated (or fast startup in Win8).

Post this to see existing partitions:
sudo parted -l

Better to use ext4 as standard partition. Many have had issues with btrfs, so not sure if all those issues resolved yet.

---

### Post by joe_schmo2 on 2015-06-12
Not sure how to switch from btrfs to ext4.  I'm considering trying to install within windows using LiLi and wubi, makes me nervous for some reason, anyone have any experience?

---

### Post by oldfred on 2015-06-12
Last supported version of wubi is 12.04.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

ext4 is Ubuntu's default, if not an advanced user why btrfs?
If reinstalling just choose default of ext4.

---

### Post by joe_schmo2 on 2015-06-12
> **oldfred said:**
> Last supported version of wubi is 12.04.

       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

ext4 is Ubuntu's default, if not an advanced user why btrfs?
If reinstalling just choose default of ext4.

I did not select btrfs, I observed a btrfs directory in my /sys directory as I was trying to install ubuntu.  I really wish Ubuntu had some sort of progress bar or debug mode where I could see what the heck was going on, because things are happening, just extremely slow. 

 I wonder if this is related to my laptop which is I think over 3 years old, or the fact that I have Windows installed.  I have in the past installed Ubuntu as the only operating system and not had any problems.

---

### Post by oldfred on 2015-06-12
Windows should not cause issues unless it needs chkdsk or is hibernated. And then only in parsing available partitions.

How much RAM and what video card/chip?
But I was able to install full Ubuntu to my laptop with 1.5GB of RAM. It was from 2 weeks before Vista was released or end of 2006. But old video chip & lower RAM runs full Ubuntu extremely slow. But I install the fallback or gnome-panel gui and that works just fine.

---

### Post by joe_schmo2 on 2015-06-12
My laptop has 4GB RAM and a I have an Intel HD Graphics video.  I have tried several Linux distributions so I don't think it's a Ubuntu issue per se.   Very frustrating though.

---

### Post by joe_schmo2 on 2015-06-14
```

Couple more things, it does appear that at some point during the install the time is changed on my laptop to GMT time, without any input from me.  Also, I see these errors reported every 8 seconds during the install.

Jun 14 07:38:49 ubuntu kernel: [   60.777837] ata1.00: exception Emask 0x0 SAct 0x2 SErr 0x0 action 0x0
Jun 14 07:38:49 ubuntu kernel: [   60.777843] ata1.00: irq_stat 0x40000008
Jun 14 07:38:49 ubuntu kernel: [   60.777848] ata1.00: failed command: READ FPDMA QUEUED
Jun 14 07:38:49 ubuntu kernel: [   60.777855] ata1.00: cmd 60/08:08:00:82:85/00:00:4a:00:00/40 tag 1 ncq 4096 in
Jun 14 07:38:49 ubuntu kernel: [   60.777855]          res 41/40:08:02:82:85/00:00:4a:00:00/6a Emask 0x409 (media error) <F>
Jun 14 07:38:49 ubuntu kernel: [   60.777859] ata1.00: status: { DRDY ERR }
Jun 14 07:38:49 ubuntu kernel: [   60.777861] ata1.00: error: { UNC }
Jun 14 07:38:49 ubuntu kernel: [   60.779794] ata1.00: configured for UDMA/100
Jun 14 07:38:49 ubuntu kernel: [   60.779812] sd 0:0:0:0: [sda] FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun 14 07:38:49 ubuntu kernel: [   60.779817] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Jun 14 07:38:49 ubuntu kernel: [   60.779821] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Jun 14 07:38:49 ubuntu kernel: [   60.779824] sd 0:0:0:0: [sda] CDB: 
Jun 14 07:38:49 ubuntu kernel: [   60.779828] Read(10): 28 00 4a 85 82 00 00 00 08 00
Jun 14 07:38:49 ubuntu kernel: [   60.779838] blk_update_request: I/O error, dev sda, sector 1250263554
Jun 14 07:38:49 ubuntu kernel: [   60.779852] ata1: EH complete

```

---

### Post by Bucky Ball on 2015-06-14
Please use code tags. See last link in my signature. Thanks.

---

### Post by oldfred on 2015-06-14
If hard drive issues, first run chkdsk in Windows an fsck on all ext4 partitions.

And check Smart Data status on drive. You can do that with Disks and tiny icon in upper right. It can run lots of tests, but passed or not is all I know. And if not passed or good drive then time for new one.

---

### Post by joe_schmo2 on 2015-06-14
I have run chkdsk /R, no problems.  I reinstalled Windows 7 without any problems 2 weeks ago.  I guess Linux is pickier with Hard Drive issues?

---

### Post by joe_schmo2 on 2015-06-15
I tried to attach this as a file but kept getting an error.  Does anyone know how to interpret this log file?  I'm sure you'll say replace the drive, but it is working perfectly fine for windows 7 and I have no money :(

```

# Smartmontools for Windows installed on 15 Jun 2015 15:47:02


smartctl 6.4 2015-06-04 r4109 [i686-w64-mingw32-win7(64)-sp1] (sf-6.4-1)
Copyright (C) 2002-15, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK6465GSX
Serial Number:    11R2S5SES
LU WWN Device Id: 5 000039 3056821a6
Firmware Version: GJ002J
User Capacity:    640,135,028,736 bytes [640 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Mon Jun 15 15:47:03 2015 ADT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (  25)	The self-test routine was aborted by
					the host.
Total time to complete Offline 
data collection: 		(  120) seconds.
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
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 193) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.


SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       2116
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       5494
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       14
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   054   054   000    Old_age   Always       -       18555
 10 Spin_Retry_Count        0x0033   209   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5401
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       260
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       139
193 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       30225
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       37 (Min/Max 6/45)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       14
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       1406
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       100
222 Loaded_Hours            0x0032   061   061   000    Old_age   Always       -       15658
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       328
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0


SMART Error Log Version: 1
ATA Error Count: 13171 (device log contains only the most recent five errors)
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


Error 13171 occurred at disk power-on lifetime: 18555 hours (773 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 92 02 82 85 6a  Error: UNC at LBA = 0x0a858202 = 176521730


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 90 00 82 85 40 00      00:02:48.649  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:02:48.649  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:02:48.649  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:02:48.648  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:02:48.648  SET FEATURES [Set transfer mode]


Error 13170 occurred at disk power-on lifetime: 18555 hours (773 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 8a 02 82 85 6a  Error: UNC at LBA = 0x0a858202 = 176521730


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 88 00 82 85 40 00      00:02:40.857  READ FPDMA QUEUED
  ec 00 01 00 00 00 00 00      00:02:37.182  IDENTIFY DEVICE
  60 08 78 00 28 03 40 00      00:02:37.070  READ FPDMA QUEUED
  60 08 70 08 28 03 40 00      00:02:37.070  READ FPDMA QUEUED
  60 08 68 00 28 03 40 00      00:02:37.070  READ FPDMA QUEUED


Error 13169 occurred at disk power-on lifetime: 18555 hours (773 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 22 02 82 85 6a  Error: UNC at LBA = 0x0a858202 = 176521730


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 20 00 82 85 40 00      00:02:25.418  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:02:25.418  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:02:25.418  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:02:25.417  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:02:25.417  SET FEATURES [Set transfer mode]


Error 13168 occurred at disk power-on lifetime: 18555 hours (773 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 1a 02 82 85 6a  Error: UNC at LBA = 0x0a858202 = 176521730


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 18 00 82 85 40 00      00:02:17.609  READ FPDMA QUEUED
  ec 00 01 00 00 00 00 00      00:02:17.543  IDENTIFY DEVICE
  60 08 08 00 18 00 40 00      00:02:17.535  READ FPDMA QUEUED
  60 08 00 a8 12 01 40 00      00:02:17.528  READ FPDMA QUEUED
  60 08 f0 00 0a 00 40 00      00:02:17.528  READ FPDMA QUEUED


Error 13167 occurred at disk power-on lifetime: 18555 hours (773 days + 3 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 c2 02 82 85 6a  Error: UNC at LBA = 0x0a858202 = 176521730


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 c0 00 82 85 40 00      00:02:09.583  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:02:09.583  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:02:09.583  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 00      00:02:09.582  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      00:02:09.582  SET FEATURES [Set transfer mode]


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%     18555         -
# 2  Short offline       Completed without error       00%     18553         -


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

---

### Post by oldfred on 2015-06-15
Drive should be ok.
SMART overall-health self-assessment test result: PASSED

---

### Post by joe_schmo2 on 2015-06-15
> **oldfred said:**
> Drive should be ok.
SMART overall-health self-assessment test result: PASSED

OK, interesting, not sure what the errors mean then.  By the way, for shits and giggles, I switched SATA mode from AHCI to IDE and tried installing, the errors were slightly different but the result was the same ie install did not get past "Preparing to Install".

I am at a loss as to what to try next.

---

### Post by oldfred on 2015-06-16
You should use AHCI. Required for SSDs so you can use trim. IDE may cause other issues.

Have you tried partitioning in advance with gparted and using Something Else?
And with the nVidia card are you using nomodeset?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by joe_schmo2 on 2015-06-16
> **oldfred said:**
> 

Have you tried partitioning in advance with gparted and using Something Else?



What do you mean "something else"?

Here is a crazy thought, what if I create and properly format a partion for linux, could i try copying the install files to the newly created partition and install from there?

---

### Post by oldfred on 2015-06-16
One of the first screens you see is the install choices. Something Else is one of those choices and lets you choose which partition you want to use for / (root) with the change button on the partitioning screen. If not partitioned in advance you can create partitions also.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by joe_schmo2 on 2015-06-19
I have created a ext4 partition using gparted, I still cannot get past "Preparing to Install" ( I never get to the "Something Else" option).  

I hate to ask the same question twice but, is it possible to copy the contents of my USB drive to my newly created partition and run the install directly from there?  I have no idea if it would make a difference but just wondering if it's worth a try.

---

### Post by oldfred on 2015-06-19
You cannot easily copy contents to partition and then install to that partition. You have to be able to boot the installer. I believe one of the installers does now let you install to a partition, not sure how you then boot it?
Are you installing in UEFI or BIOS boot mode. And if UEFI have you set UEFI settings correctly?

Are you using nomodeset?
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

    

I do copy ISO to a partition on my hard drive to install to my SSD or vice versa, but have to use grub2 to boot it.
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by joe_schmo2 on 2015-06-20
I am installing in BIOS boot mode and I have tried nomodeset.

I have another question, can you tell me why Ubuntu thinks I am using a CDROM?

This is my casper,log

```

Generating locales...
  en_US.UTF-8... done
Generation complete.
pwconv: failed to change the mode of /etc/passwd- to 0600
Using CD-ROM mount point /cdrom/
Identifying... [e50d1a0f483f1950975883421fb6963e-2]
Scanning disc for index files...
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)'
This disc is called: 
'Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)'
Copying package lists...gpgv: Signature made Wed Apr 22 12:30:00 2015 UTC using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 15.04 _Vivid Vervet_ - Release amd64 (20150422)]/ vivid main restricted
Repeat this process for the rest of the CDs in your set.


```

---

### Post by oldfred on 2015-06-20
Did you use dd to create flash drive?

And it still is the image of the CD, now DVD installer, just on a flash drive.

---

### Post by joe_schmo2 on 2015-06-21
I used unetbootin, I've also tried Lili USB Creator and Universal USB Creator.

Is this the problem?

---

### Post by oldfred on 2015-06-21
Should not be.
I believe one of the installers did not work with the new UEFI. But unetbootin has worked for most. A few have had issues and used other installers.
And some flash drives have had issues.
But in all those cases it would not start at all.
I still think it is either some settings in BIOS or boot parameters. But I do not know AMD systems. I do have an older nVidia and up until most recent versions have always had to use nomodeset. Some of the very new Maxwell based card do have issues, but I do not think your model is that.

This is Intel, with newest Maxwell.
 Asus z97-A with nVidia GTX 970 Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)

---

### Post by joe_schmo2 on 2015-06-22
Well, I finally got Ubuntu installed !!

I know that before I partitioned my hard drive with gparted that I sat at the "Preparing to Install" screen for over 2 hours.  I can't say 100% that it was because I partitioned with gparted before I attempted to install but this time it took about 1 hr and 50 minutes to get past that screen ("Preparing to Install").   Bottom line the install took over 5 hours, can't say exactly how long because I finally went to bed and when I woke up the install was completed.

I have a couple of issues still but I will open another thread in the appropriate forum.

Thanks for engaging me while I tried to get Ubuntu installed, I probably would have given up without someone to listen to my whining :)


Do I need to close this thread?  Don't know how to if so.

---

### Post by sammiev on 2015-06-22
> **joe_schmo2 said:**
> Well, I finally got Ubuntu installed !!

I know that before I partitioned my hard drive with gparted that I sat at the "Preparing to Install" screen for over 2 hours.  I can't say 100% that it was because I partitioned with gparted before I attempted to install but this time it took about 1 hr and 50 minutes to get past that screen ("Preparing to Install").   Bottom line the install took over 5 hours, can't say exactly how long because I finally went to bed and when I woke up the install was completed.

I have a couple of issues still but I will open another thread in the appropriate forum.

Thanks for engaging me while I tried to get Ubuntu installed, I probably would have given up without someone to listen to my whining :)


Do I need to close this thread?  Don't know how to if so.

Hi Joe,

You never started this thread, so you can not close it. :)

---

### Post by Bucky Ball on 2015-06-23
In fact, only staff can close it and we don't close solved threads. The original poster marks them as solved from 'Thread Tools' and they are not closed, they stay open for further discussion, if there is one, and the 'solved' tag serves to help others. ;)

---

