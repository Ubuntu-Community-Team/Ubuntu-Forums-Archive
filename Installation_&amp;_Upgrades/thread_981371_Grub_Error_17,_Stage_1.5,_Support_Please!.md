---
title: "Grub Error 17, Stage 1.5, Support Please!"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by DanTheMan01 on 2008-11-13
Ive searched all these forums and about 17 other's, & still no luck, This is a very popular question around but i cannot seem to fix it, Could you please tell me how to fix this Error ill give you as much Detail as possible.

I have a Dell Laptop & I turn on my computer the dell logo shows up Saying Press f2 = Bios / F12 = Boot From??

It then says:

Grub Loading Stage1.5

GRUB Loading, please wait...

I then have not got a clue what to do, I only have ubuntu installed & I tryd booting from ubuntu CD by putting in the 8.04 LIVE CD, And tryd booting from it and i get a few error's, If you would like to know the error ill provide them with you as much detail as possible. Something about Block Error's. I saw

I can reformat back to windows, But i have important file's on my ubuntu machine and i need them so i really do need to fix this, Or less there's a possible way to backup my file's and then i could reformat back to ubuntu Which would work. But which ever is easier to do Either fix the error, or backup my file's. I do have the Ubuntu live CD So if that come's in handy i can use this.

But if you could just explain on what to do Since I'm new to this and i have not got a clue on how to fix this error. Please provide me with ubuntu support as much as possible on how to fix this error or how to backup my File's on my dell ubuntu system.

If you need more Detail on my machine to help you I'm happy to provide information to help solve this.

Please Help.

- Regards ):P

---

### Post by tvtech on 2008-11-13
if this is a production machine I think you might be in trouble.  

it sounds like you've got a hdd death, or near death.  

error 17 usually comes up when you have an old bios that has problems recognizing sized beyond 128 gb..  I've got an old desktop with this problem and has to build a boot partition of 2 gig on a 250 gig drive to make it work.  

but it's a pentium III.   

your going to need to find a live CD/DVD of some sort, I recommend knoppix myself. and rescue your data then do a drive check to see if you've got real problems with it before reformatting it.

---

### Post by DanTheMan01 on 2008-11-13
> **tvtech said:**
> if this is a production machine I think you might be in trouble.  

it sounds like you've got a hdd death, or near death.  

error 17 usually comes up when you have an old bios that has problems recognizing sized beyond 128 gb..  I've got an old desktop with this problem and has to build a boot partition of 2 gig on a 250 gig drive to make it work.  

but it's a pentium III.   

your going to need to find a live CD/DVD of some sort, I recommend knoppix myself. and rescue your data then do a drive check to see if you've got real problems with it before reformatting it.

Hello, Thank you for your response.

Ohhh NO, & Yes i only have something like an 120 HDD, and 2 GB Ram, I have a few spare Cd's. & a spare 7 GB USB, which is blank, I have a few 700 MB Cd's which are blank also. If you could provide me with the ISO of knoppix, I'll burn it to the CD or USB, could you provide me on what i will need to do to fix this. If you can using knoppix or some other sort of way to fix this. 

Thank you
- Regards

---

### Post by caljohnsmith on 2008-11-13
In order to troubleshoot your problem, you really need to be able to boot some Live CD. You could try downloading maybe an earlier version of Ubuntu (7.10) and see if that works, or maybe try another debian based distro like PCLinuxOS. But the bottom line is you will need to boot some Live CD in order to troubleshoot. You can go to [www.distrowatch.com](www.distrowatch.com) and find links to all the major distributions. Once you have a Live CD that boots OK, let me know and I can help you troubleshoot your Grub problem if you want. :)

---

### Post by DanTheMan01 on 2008-11-13
> **caljohnsmith said:**
> In order to troubleshoot your problem, you really need to be able to boot some Live CD. You could try downloading maybe an earlier version of Ubuntu (7.10) and see if that works, or maybe try another debian based distro like PCLinuxOS. But the bottom line is you will need to boot some Live CD in order to troubleshoot. You can go to [www.distrowatch.com](www.distrowatch.com) and find links to all the major distributions. Once you have a Live CD that boots OK, let me know and I can help you troubleshoot your Grub problem if you want. :)

Thank you for your response.

That would be great I'll find a CD Ubuntu Old CD, And burn it to cd and let you know once it's done.

Thank you for Your support.
- regards

---

### Post by DanTheMan01 on 2008-11-13
I installed 7.10, But the Rescue thing isnt there,

what shall i do?,

- regards

---

### Post by caljohnsmith on 2008-11-13
Do you mean you can boot the Ubuntu 7.10 Live CD? If you can, then choose the option "try Ubuntu without changing my computer", and then when you get to the desktop, go to Applications > Accessories > Terminal, and post the output of:
```
sudo fdisk -lu
```
And just to clarify, you are getting the Grub error 17 before seeing the Grub menu? When it was working, did you see the Grub menu or did you boot directly into Ubuntu on start up?

---

### Post by DanTheMan01 on 2008-11-13
there's:

start or install ubuntu
start ubuntu in safe graphics mode
install with driver update cd
oem install (for manufavturer)
check cd for defects
memory test
boot from first hard disk

F1 HELP - F2 LANGUAGE - F3 KEYMAP - F4 VGA - F5 ACCESSIBILITY - F6 OTHER OPTIONS

- regards

---

### Post by caljohnsmith on 2008-11-13
Choose the first option "Start or install Ubuntu", and once you get to the desktop, please post the output of the previous command I gave. And also, please answer, are you getting the Grub error 17 before seeing the Grub menu on start up? When it was working, did you see the Grub menu or did you boot directly into Ubuntu on start up?

---

### Post by DanTheMan01 on 2008-11-13
> **caljohnsmith said:**
> Choose the first option "Start or install Ubuntu", and once you get to the desktop, please post the output of the previous command I gave. And also, please answer, are you getting the Grub error 17 before seeing the Grub menu on start up? When it was working, did you see the Grub menu or did you boot directly into Ubuntu on start up?

no, the logon screen dont load atall I carnt get into the Desktop or anything. It just says error 17 right away, I dont see any Grub menu.

Hey dude, i erm tryd to do what you said, start ubuntu 7.10 The first option when i boot from 7.10 cD and i get this:

Click to View larger:
[[IMG]http://i38.tinypic.com/1zyjvoo_th.jpg[/IMG]]("http://i38.tinypic.com/1zyjvoo.jpg")

---

### Post by caljohnsmith on 2008-11-13
Well, you could try some other Live CDs, but it looks like you might be having some sort of hardware problem.

---

### Post by DanTheMan01 on 2008-11-14
What Cd's Would you recommend?

---

### Post by caljohnsmith on 2008-11-14
You could try the Knoppix Live CD mentioned earlier, or other distros you could try would be Mandriva, PCLinuxOS, etc. You just need to find one that boots OK, but you may not be able to if you have a hardware problem. You'll just have to try.

---

### Post by DanTheMan01 on 2008-11-15
I have got Fedora Booted on my machine that worked and i can see the terminal, So what should i do? If this help's, I can access the Fedora desktop with all main stuff now such as terminal etc..

If this help's, Hope i can do something now What should i do? Now i have booted into fedora anything i can do to help me backing up my file's or fixing the grub error 17?

Fdisk - Click Below To View (I was not on the desktop):
[[IMG]http://i34.tinypic.com/vio8qo_th.jpg[/IMG]]("http://i34.tinypic.com/vio8qo.jpg")

This is me logged in as root on the desktop,:
[[IMG]http://i34.tinypic.com/2118c3q_th.jpg[/IMG]]("http://i34.tinypic.com/2118c3q.jpg")

Any help would be great.

Thanks alot
-Regards

---

### Post by caljohnsmith on 2008-11-15
OK, while you are logged into the terminal as root, post the output of:
```
fsck -y /dev/sda1
```
If that completes successfully, then do:
```
mount /dev/sda1 /mnt
nautilus /mnt
```
And the Nautilus file browser should show the Ubuntu root file system. You can then browse to /home/<your username> and I assume that's where you keep all your files. You can back up your important files from there if you want.

Next try:
```
grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
And please post the output of all the above commands. Once you've backed up all your files, and if the Grub commands complete successfully, reboot and see if you get the Grub menu. Let me know how it goes.

---

### Post by DanTheMan01 on 2008-11-15
Hey, Thanks for your reply.

Sorry for the kinda late reply, i did try and do this by the commands you gave me, I tryd the first command please view:

Click to View Larger:
[[IMG]http://i36.tinypic.com/14xjp50_th.jpg[/IMG]]("http://i36.tinypic.com/14xjp50.jpg")

What shall i do?

Thanks for Support
- Regards.

---

### Post by caljohnsmith on 2008-11-15
OK, that's definitely not a good sign that fsck returned that error. I don't remember how to install packages in Fedora since it is a Red Hat based distro, but see if you can find and install the "smartmontools" package that is hopefully in their repositories. Once you can do that, let me know and we can work from there.

---

### Post by DanTheMan01 on 2008-11-15
I'm on my laptop right now with fedora it says: 

```

[root@localhost ~]# yum install smartmontools
Loaded plugins: refresh-packagekit
Setting up Install Process
Parsing package install arguments
Package 1:smartmontools-5.38-2.fc9.i386 already installed and latest version
Nothing to do
[root@localhost ~]# 

```

Any idea how to find/start smartmontools tho?
- Regards

---

### Post by caljohnsmith on 2008-11-15
Sure, here is how you can run the smartmontools: first do the following to save the current health status parameters of your HDD to a file on your desktop:
```
smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
```
Then run:
```
smartctl -t long /dev/sda
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
smartctl -H /dev/sda
```
And let me know the results.

---

### Post by DanTheMan01 on 2008-11-15
Thanks for the reply.

Here is what i did, If it is correct or not:
```

[root@localhost ~]# smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
[root@localhost ~]# smartctl -t long /dev/sda
smartctl version 5.38 [i386-redhat-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 58 minutes for test to complete.
Test will complete after Sat Nov 15 16:34:23 2008

Use smartctl -X to abort test.
[root@localhost ~]# smartctl -a /dev/sda | grep -A 1 -i "self-test execution status
> smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
> smartctl -H /dev/sda
> 

```

Here is the sda_health_before_test From my Desktop:
```

smartctl version 5.38 [i386-redhat-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD1200BEVS-75UST0
Serial Number:    WD-WXCY07158724
Firmware Version: 01.01A01
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat Nov 15 15:36:15 2008 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (4560) seconds.
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
recommended polling time: 	 (  58) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   160   151   021    Pre-fail  Always       -       991
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2895
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000e   200   200   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   092   092   000    Old_age   Always       -       5852
 10 Spin_Retry_Count        0x0012   100   099   051    Old_age   Always       -       1
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       984
192 Power-Off_Retract_Count 0x0032   199   199   000    Old_age   Always       -       781
193 Load_Cycle_Count        0x0032   171   171   000    Old_age   Always       -       88088
194 Temperature_Celsius     0x0022   098   082   000    Old_age   Always       -       45
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       1
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 465 (device log contains only the most recent five errors)
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

Error 465 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 04 00 3f 00 00 00 08      00:26:21.466  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:26:21.466  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:26:21.465  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:26:21.465  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:26:21.465  READ NATIVE MAX ADDRESS EXT

Error 464 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 04 00 3f 00 00 00 08      00:26:17.349  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:26:17.349  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:26:17.348  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:26:17.348  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:26:17.348  READ NATIVE MAX ADDRESS EXT

Error 463 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 04 00 3f 00 00 00 08      00:26:13.233  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:26:13.233  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:26:13.232  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:26:13.232  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:26:13.232  READ NATIVE MAX ADDRESS EXT

Error 462 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 04 00 3f 00 00 00 08      00:26:09.249  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:26:09.249  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:26:09.249  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:26:09.248  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:26:09.248  READ NATIVE MAX ADDRESS EXT

Error 461 occurred at disk power-on lifetime: 5851 hours (243 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 41 00 00 40

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 04 00 3f 00 00 00 08      00:26:05.133  READ FPDMA QUEUED
  27 00 00 00 00 00 00 08      00:26:05.133  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 00 08      00:26:05.132  IDENTIFY DEVICE
  ef 03 46 00 00 00 00 08      00:26:05.132  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 00 08      00:26:05.132  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      5852         65
# 2  Short offline       Completed without error       00%         1         -
# 3  Short offline       Completed without error       00%         0         -
# 4  Short offline       Interrupted (host reset)      90%         0         -

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

Thank you
-Regards

---

### Post by caljohnsmith on 2008-11-15
> **DanTheMan01 said:**
> 
[root@localhost ~]# smartctl -a /dev/sda | grep -A 1 -i "self-test execution status
> smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
> smartctl -H /dev/sda
> 
[/code]

Be sure to include the last double quote in that command above:
```
smartctl -a /dev/sda | grep -A 1 -i "self-test execution status[COLOR="Red"]"[/COLOR]
```
That is why you got the ">" prompt. You can break out of it by hitting "Ctrl-C". Let me know in an hour when the test completes how it went.

---

### Post by DanTheMan01 on 2008-11-15
Thanks for the reply I did the commands you said, 

I think this is correct:
```

[root@localhost ~]# cd /
[root@localhost /]# smartctl -a /dev/sda > ~/Desktop/sda_health_before_test.txt
[root@localhost /]# smartctl -t long /dev/sda
smartctl version 5.38 [i386-redhat-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 58 minutes for test to complete.
Test will complete after Sat Nov 15 16:42:41 2008

Use smartctl -X to abort test.
[root@localhost /]# smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
[root@localhost /]# smartctl -a /dev/sda > ~/Desktop/sda_health_after_test.txt
[root@localhost /]# 
[root@localhost /]# smartctl -H /dev/sda
smartctl version 5.38 [i386-redhat-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

[root@localhost /]# 

```

What shall i do ?

Thank you
- Regards

---

### Post by MasterSander on 2008-11-15
You should reinstall the grub as well while you're using a live cd.Caljohnsmith mentioned it earlier, it something like ```
 grub 
``` to launch the program, then enter the commands he gave you. I had error 17 before as well. But also follow the other advice he gave you to check if your hd is screwed up.

---

### Post by DanTheMan01 on 2008-11-15
> **MasterSander said:**
> You should reinstall the grub as well while you're using a live cd.Caljohnsmith mentioned it earlier, it something like ```
 grub 
``` to launch the program, then enter the commands he gave you. I had error 17 before as well. But also follow the other advice he gave you to check if your hd is screwed up.

Thanks for the info:

```

[root@localhost ~]# grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]
grub> 

```

Any help?

- Regards

---

### Post by caljohnsmith on 2008-11-15
> **DanTheMan01 said:**
> ```

[root@localhost /]# smartctl -a /dev/sda | grep -A 1 -i "self-test execution status"
Self-test execution status:      ([COLOR="Red"] 121)	The previous self-test completed having
					the read element of the test failed.[/COLOR]

```

Unfortunately, based on that error above, it looks to me like your HDD is failing. The SMART test wasn't even able to complete. It might be though that you are experiencing a hardware issue with your RAM or motherboard instead, because you have had lots of problems getting even Live CDs to boot. I would recommend downloading the "[Ultimate Boot CD]("http://www.ultimatebootcd.com")" and try running some more HDD diagnostic tests on your HDD to get a better idea if your HDD is truly the problem. Also, I would be sure to run the "memtest86+" test from the Ultimate Boot CD to check your RAM. 

Also, if you want to try and recover data off that drive, you could try "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", but you'll need a large drive to save all the recovered files to it. Good luck and let me know how it goes. 

P.S. Running the "grub" command will unfortunately not help you at this point.

---

### Post by DanTheMan01 on 2008-11-15
> **caljohnsmith said:**
> Unfortunately, based on that error above, it looks to me like your HDD is failing. The SMART test wasn't even able to complete. It might be though that you are experiencing a hardware issue with your RAM or motherboard instead, because you have had lots of problems getting even Live CDs to boot. I would recommend downloading the "[Ultimate Boot CD]("http://www.ultimatebootcd.com")" and try running some more HDD diagnostic tests on your HDD to get a better idea if your HDD is truly the problem. Also, I would be sure to run the "memtest86+" test from the Ultimate Boot CD to check your RAM. 

Also, if you want to try and recover data off that drive, you could try "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")", but you'll need a large drive to save all the recovered files to it. Good luck and let me know how it goes. 

P.S. Running the "grub" command will unfortunately not help you at this point.

Thanks for the reply.

Do i download 'http://pharry.eu/data/ubcd411.iso' Which is the v4 version, and burn to a cd?, and then restart my computer and then boot from cd?

Thanks
-Regards.

---

### Post by caljohnsmith on 2008-11-15
> **DanTheMan01 said:**
> Thanks for the reply.

Do i download 'http://pharry.eu/data/ubcd411.iso' Which is the v4 version, and burn to a cd?, and then restart my computer and then boot from cd?

Thanks
-Regards.
Yes, that should work fine.

---

