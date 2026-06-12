---
title: "Ubuntu installation error: input/output error on /dev/sda"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by samuel15 on 2014-10-03
I was installing Ubuntu desktop onto my laptop via USB and I got this error, input/output error on /dev/sda. I don't really know how to fix it so does anyone have any help?

Here is the full story:

I had Windows 8.1 on the laptop but I didn't want it anymore as I got a new laptop (basically, I don't want to dual boot I want to remove windows and install Ubuntu). I have installed Lubuntu on my friends old laptop so I already knew the steps of writing the image, booting it from a USB etc. I burned the image using UniversalUSBInstaller. So far so good. I plugged it in, changed it to automatically boot from the USB first in the BIOS and I selected try Ubuntu before installing to check everything was working ok. It was, so I opened the installer and the installation stopped about 20mins through with an error saying, the installer had crashed. I thought it was just a bug so I tried again and got the same error. I plugged the USB back into my windows laptop and re-downloaded the .iso image file, formatted the USB and then burned it back onto the USB. I plugged it back in, the same thing booted, so far so good but then I got the error input/output error on /dev/sda when I get to selecting the time on the installer. I tried and tried again but I kept getting the same error at the same place. I looked on the internet about this and was told to change the hard drive (SATA) mode onto ACHI. It was already on ACHI by default. I changed it to IDE, no luck, then I changed it back, still no luck. Does anyone know why its doing this and how I can fix it?

I thought I would mention that I am installing Ubuntu 14.04.1 64-bit
Also, it did wipe windows off I can't boot it back into windows (note: I didn't have plans on dual booting it anyways) 

Thank you 

- samuel15 / WeKnowMC

---

### Post by matt_symes on 2014-10-03
Hi

This is going to sound rather a dumb question but is /dev/sda the usb pendrive or the hard disc you are trying to install Ubuntu onto ? I forget which it is.

If sda is the usb drive then it could be a corrupted download (did you check the ISO signature ?) or failing pendrive (have you tried a different pen drive ?).

If sda is the hard drive then it may be bad sectors on the hard drive. If the drive has it, i would run a smart test, and either a badblock test or zero the entire drive sector by sector in an attempt to force the drives firmware to mark that sector as bad.

Kind regards

---

### Post by samuel15 on 2014-10-03
Yes, /dev/sda is the hard drive

I have checked the ISO signature and everything seems to be ok about the USB.

Also, how would I run smart tests and badlock tests? I'm pretty new to this stuff.

---

### Post by matt_symes on 2014-10-03
Hi

> **samuel15 said:**
> Yes, /dev/sda is the hard drive

I have checked the ISO signature and everything seems to be ok about the USB.

You can double check that by using another pen drive and the same ISO. It may be redundant but you would have pretty much eliminated the ISO and pen drive side of thing.

> Also, how would I run smart tests and badlock tests?

Anyway, boot into the Live environment on the USB stick and don't select any option to install to the hard drive.

Connect to the Internet, open a terminal and type

```
sudo apt-get install smartmontools
```

After the package is installed type this into the terminal.

```
sudo smartctl -t long /dev/sda
```

It will take a while (dependent on drive size) and should display the expected finish time when you type the above command. Give it an extra 5 minutes after that and then type

```
sudo smartctl -a /dev/sda
```

Copy and paste the output from that last command into your next post between code tags.

A SMART test is not a fool proof test as there are a number of ways it can be fooled however it's a good place to start.

Let's see what it returns and take it from there.

> I'm pretty new to this stuff.

You're doing better than me. I could not even remember which device sda was :)

Kind regards

---

### Post by samuel15 on 2014-10-03
Ok, I've done everything you've said and here are the results:

```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-32-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org
 
=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA (AF)
Device Model:     WDC WD3200BPVT-22JJ5T0
Serial Number:    WD-WX81E32SJV39
LU WWN Device Id: 5 0014ee 602bda8f2
Firmware Version: 01.01A01
User Capacity:    320,072,933,376 bytes [320 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Fri Oct  3 20:50:16 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled
 
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.
 
General SMART Values:
Offline data collection status:  (0x00)            Offline data collection activity
                                                            was never started.
                                                            Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 241)   Self-test routine in progress...
                                                            10% of test remaining.
Total time to complete Offline 
data collection:                        ( 7260) seconds.
Offline data collection
capabilities:                              (0x7b) SMART execute Offline immediate.
                                                            Auto Offline data collection on/off support.
                                                            Suspend Offline collection upon new
                                                            command.
                                                            Offline surface scan supported.
                                                            Self-test supported.
                                                            Conveyance Self-test supported.
                                                            Selective Self-test supported.
SMART capabilities:            (0x0003)            Saves SMART data before entering
                                                            power-saving mode.
                                                            Supports SMART auto save timer.
Error logging capability:        (0x01)   Error logging supported.
                                                            General Purpose Logging supported.
Short self-test routine 
recommended polling time:     (   2) minutes.
Extended self-test routine
recommended polling time:     (  75) minutes.
Conveyance self-test routine
recommended polling time:     (   5) minutes.
SCT capabilities:                (0x7035)   SCT Status supported.
                                                            SCT Feature Control supported.
                                                            SCT Data Table supported.
 
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       8518
  3 Spin_Up_Time            0x0027   141   118   021    Pre-fail  Always       -       1941
  4 Start_Stop_Count        0x0032   086   086   000    Old_age   Always       -       14641
  5 Reallocated_Sector_Ct   0x0033   133   133   140    Pre-fail  Always   FAILING_NOW 561
  7 Seek_Error_Rate         0x002e   154   154   000    Old_age   Always       -       11461
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2531
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1739
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       4017
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       64
193 Load_Cycle_Count        0x0032   071   071   000    Old_age   Always       -       387328
194 Temperature_Celsius     0x0022   104   100   000    Old_age   Always       -       39
196 Reallocated_Event_Count 0x0032   191   191   000    Old_age   Always       -       9
197 Current_Pending_Sector  0x0032   200   001   000    Old_age   Always       -       17
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
 
SMART Error Log Version: 1
Warning: ATA error count 18047 inconsistent with error log pointer 1
 
ATA Error Count: 18047 (device log contains only the most recent five errors)
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
 
Error 18047 occurred at disk power-on lifetime: 2530 hours (105 days + 10 hours)
  When the command that caused the error occurred, the device was in standby mode.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 03 00 00 00 a0  Device Fault; Error: ABRT
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 90 03 00 00 00 a0 08      00:04:30.889  SET FEATURES [Disable SATA feature]
  ec 00 01 00 00 00 40 08      00:04:30.326  IDENTIFY DEVICE
  ef 05 fe 00 00 00 40 08      00:04:30.325  SET FEATURES [Enable APM]
  ec 00 01 00 00 00 40 08      00:04:30.251  IDENTIFY DEVICE
  ef 10 02 00 00 00 a0 08      00:04:27.606  SET FEATURES [Enable SATA feature]
 
Error 18046 occurred at disk power-on lifetime: 2530 hours (105 days + 10 hours)
  When the command that caused the error occurred, the device was in standby mode.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 fe 00 00 00 40  Device Fault; Error: ABRT
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 05 fe 00 00 00 40 08      00:04:30.325  SET FEATURES [Enable APM]
  ec 00 01 00 00 00 40 08      00:04:30.251  IDENTIFY DEVICE
  ef 10 02 00 00 00 a0 08      00:04:27.606  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.605  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:04:27.604  SET FEATURES [Set transfer mode]
 
Error 18045 occurred at disk power-on lifetime: 2530 hours (105 days + 10 hours)
  When the command that caused the error occurred, the device was in standby mode.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 02 00 00 00 a0  Device Fault; Error: ABRT
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:04:27.606  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.605  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 08      00:04:27.604  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:04:27.604  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.603  IDENTIFY DEVICE
 
Error 18044 occurred at disk power-on lifetime: 2530 hours (105 days + 10 hours)
  When the command that caused the error occurred, the device was in standby mode.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 46 00 00 00 a0  Device Fault; Error: ABRT
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 03 46 00 00 00 a0 08      00:04:27.604  SET FEATURES [Set transfer mode]
  ef 10 02 00 00 00 a0 08      00:04:27.604  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.603  IDENTIFY DEVICE
  c8 00 08 00 00 00 e0 08      00:04:27.603  READ DMA
  ef 10 02 00 00 00 a0 08      00:04:27.602  SET FEATURES [Enable SATA feature]
 
Error 18043 occurred at disk power-on lifetime: 2530 hours (105 days + 10 hours)
  When the command that caused the error occurred, the device was in standby mode.
 
  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 61 02 00 00 00 a0  Device Fault; Error: ABRT
 
  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  ef 10 02 00 00 00 a0 08      00:04:27.604  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.603  IDENTIFY DEVICE
  c8 00 08 00 00 00 e0 08      00:04:27.603  READ DMA
  ef 10 02 00 00 00 a0 08      00:04:27.602  SET FEATURES [Enable SATA feature]
  ec 00 00 00 00 00 a0 08      00:04:27.601  IDENTIFY DEVICE
 
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



I hope this helps! :D

---

### Post by matt_symes on 2014-10-03
Hi

> **samuel15 said:**
> I hope this helps! :D

From the summary alone...

> SMART overall-health self-assessment test result: FAILED! 
Drive failure expected in less than 24 hours. SAVE ALL DATA.

...and i have not even looked at the rest of the report yet.

**EDIT:**

> 5 Reallocated_Sector_Ct   0x0033   133   133   140    Pre-fail  Always   FAILING_NOW 561

SMART is telling you that the drive has reallocated many sectors already.

**EDIT2:**

You also have a number of aborted ATA commands.

> ATA Error Count: 18047 (device log contains only the most recent five errors)

You can, if you like, put the drive into another machine and run the same SMART test. It will eliminate problems with the chipsets on the motherboard, however.....

Kind regards

---

### Post by samuel15 on 2014-10-03
So..... what can I do?

I don't really understand much of this.

---

### Post by matt_symes on 2014-10-03
Hi

> **samuel15 said:**
> So..... what can I do?

I don't really understand much of this.

Check my edits to my post above, especially edit2.

Personally though, i think it may be time to procure a new hard drive.

Kind regards

---

### Post by grahammechanical on 2014-10-03
Why did you buy a new laptop? Was this laptop giving you trouble when using Windows 8? It is looking like it needs a replacement hard drive.

---

### Post by matt_symes on 2014-10-03
Hi

> **grahammechanical said:**
> Why did you buy a new laptop? Was this laptop giving you trouble when using Windows 8? It is looking like it needs a replacement hard drive.

Good point. Is the laptop still under warranty ?

Kind regards

---

### Post by samuel15 on 2014-10-03
Ok thanks. I'm not too sure whether I'm going to buy a new hard drive or not, but I can decide later.

Is there any way to fix the hard drive without paying or buying a new one?

Sorry, I didn't explain it very well.

The laptop used to be mine until I bought a new gaming one. I gave the the old laptop to my brother. He doesn't need it anymore so I thought I would install Ubuntu because I would like a linux computer.

I wouldn't have thought so. It was bought a good 2 years ago. I'll check tomorrow if it is in warranty but I doubt it.

Ok, I just talked to my brother and he said that he had managed to get viruses on it before he gave it back to me. I didn't really check if it booted (I should have) but he said that windows 8.1 wouldn't boot.

---

### Post by matt_symes on 2014-10-03
Hi

Ask him if he dropped it ;)

Kind regards

---

### Post by matt_symes on 2014-10-03
Hi

A thought. You can remove the failing hard drive and create a persistent USB pen drive.

You can boot the laptop off that pen drive and use its persistent storage as a small hard drive. 

It will not have much space but it will be a bootable Ubuntu laptop and you can use it until you decide to buy a new hard drive or not.

Kind regards

---

### Post by samuel15 on 2014-10-04
> **matt_symes said:**
> Hi

A thought. You can remove the failing hard drive and create a persistent USB pen drive.

You can boot the laptop off that pen drive and use its persistent storage as a small hard drive. 

Kind regards

Ok, I think that's what I'm going to do.
The only problem is, how do I do it? :)

---

### Post by matt_symes on 2014-10-04
Hi

> **samuel15 said:**
> Ok, I think that's what I'm going to do.
The only problem is, how do I do it? :)

Read this for some background first.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I assume you currently only have access to Windows boxen ?

Kind regards

---

### Post by samuel15 on 2014-10-19
I'm sorry that its been a while because I have been quite busy.


I tried to get ubuntu to boot off a 16GB USB.


> [COLOR=#000000]Read this for some background first.[/COLOR]

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

I have looked at this and tried a few things but, no luck



> [COLOR=#000000]I assume you currently only have access to Windows boxen ?[/COLOR]

Sorry but I have no idea what windows boxen is.


Also, I had a look at this youtube video: [https://www.youtube.com/watch?v=KDM2LqFoHv4](https://www.youtube.com/watch?v=KDM2LqFoHv4)
Everything went well until I restarted it after the installation had finished to the USB. What happened was it just gave me a blank flashing cursor thing like usual.



I really feel like throwing this laptop out the window :D

Anyways, does anyone have any ideas

---

### Post by matt_symes on 2014-10-19
Hi

Did you set the boot order and priority to boot from the USB stick in the BIOS ?

Did you see the POST screen text when first starting up the PC with the with the pen drive inserted ?

Do you see any text at all when starting the PC ?

How about if you remove the USB stick. Do you see any text then ?

Just trying to get some idea of what is happening when you start the PC with and without the USB stick inserted so please answer all the questions.

BTW: Windows Boxen == Windows PC :)

Kind regards

---

### Post by samuel15 on 2014-10-19
Hi

> [COLOR=#000000]Did you set the boot order and priority to boot from the USB stick in the BIOS ?[/COLOR]
Yes, my boot order is:
[LIST=1]
[*]USB Hard Disk
[*]USB Key
[*]USB Floppy
[*]USB CD/DVD
[*]UEFI
[*]Network
[*]CD/DVD
[*]Hard Disk
[/LIST]

> [COLOR=#000000]Did you see the POST screen text when first starting up the PC with the with the pen drive inserted ?[/COLOR]

[COLOR=#000000]Do you see any text at all when starting the PC ?[/COLOR]

[COLOR=#000000]How about if you remove the USB stick. Do you see any text then ?[/COLOR]

Ok, the same thing happens with the pen drive/USB in or out.

What happens when I start it up is the ADVENT (computer make) logo comes on for a few seconds then the cursor thing comes up (just like a black screen with the _ cursor)
Also, I don't see any text and can't type anything.


Finally, no I don't have windows on it because when I first tried to install ubuntu, I clicked erase windows then got the input/output error on /dev/sda.

---

### Post by matt_symes on 2014-10-19
Hi
> 
Ok, the same thing happens with the pen drive/USB in or out.

What happens when I start it up is the ADVENT (computer make) logo comes  on for a few seconds then the cursor thing comes up (just like a black  screen with the _ cursor)
Also, I don't see any text and can't type anything.

Sounds like it's not recognising the USB stick as a bootable USB stick for some reason.

Have you tried selecting 'USB key' as the boot device ?

Can you disable all other boot devices ?

Did you install Ubuntu on the stick as MSDOS and UEFI/GPT ? This may be a cause of the problem as i have some PC's that just will not boot UEFI/GPT.

Can you use the USB stick and boot it on any other PCs ?

Kind regards

---

### Post by samuel15 on 2014-10-19
Hi

> [COLOR=#000000]Have you tried selecting 'USB key' as the boot device ?[/COLOR]
Yes, it just does the same cursor thing (_)


 > [COLOR=#000000]Can you disable all other boot devices ?[/COLOR]
I disabled everything but the USB devices and with the USB plugged in, the cursor thing comes up, with it unplugged it boots back into the BIOS


> [COLOR=#000000]Did you install Ubuntu on the stick as MSDOS and UEFI/GPT ? This may be a cause of the problem as i have some PC's that just will not boot UEFI/GPT.[/COLOR]
I really don't know. I didn't do anything about that so I'm guessing no.


> [COLOR=#000000]Can you use the USB stick and boot it on any other PCs ?[/COLOR]
I put it on an old computer running lubuntu and I got the same thing. I'm guessing its a problem with the USB then. Bare in mind I tested it out on an old computer which is also the same make (advent) so that might be why its not working. I really don't know.

---

### Post by matt_symes on 2014-10-19
Hi

> I put it on an old computer running lubuntu and I got the same thing.  I'm guessing its a problem with the USB then. Bare in mind I tested it  out on an old computer which is also the same make (advent) so that  might be why its not working. I really don't know.

This does sound like a problem with the USB stick. 

It looks like your PCs do not see it as a bootable device so it may not be a problem with the computers but the USB stick itself.

I've just been watching the youtube video. 

It shows creating a bootable DVD on Windows. Did you create a bootable DVD and if so, did you use Windows or Linux ?

Kind regards

---

### Post by samuel15 on 2014-10-19
> [COLOR=#000000] Did you create a bootable DVD and if so, did you use Windows or Linux ?[/COLOR]
I didn't use a DVD because I didn't have a spare one. Instead I used another USB. So I had one 4GB USB which was installing to the 16GB USB. Also, I had made the 4GB istallation USB with universal usb installer on windows.

---

### Post by matt_symes on 2014-10-19
Hi

> 
I didn't use a DVD because I didn't have a spare one. Instead I used  another USB. So I had one 4GB USB which was installing to the 16GB USB.  Also, I had made the 4GB istallation USB with universal usb installer on  windows.

I see. That youtube tutorial looked alright.

Can you plug the 16GB USB stick into your Lubuntu machine and type

```
sudo parted -l
```

If you need to install parted under Lubuntu (I have not used it in a while)

```
sudo apt-get install parted
```

Can you post the results back here.

Kind regards

---

### Post by samuel15 on 2014-10-19
Ok, I've done that, here are the results:

```
Model: SanDisk Cruzer Edge (scsi)Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  500MB   499MB   primary   ext4            boot
 2      501MB   11.5GB  11.0GB  extended
 5      501MB   7500MB  6999MB  logical   ext4
 6      7502MB  11.5GB  3999MB  logical   linux-swap(v1)
```

---

### Post by matt_symes on 2014-10-19
Hi

> **samuel15 said:**
> Ok, I've done that, here are the results:

```
Model: SanDisk Cruzer Edge (scsi)Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type      File system     Flags
 1      1049kB  500MB   499MB   primary   ext4            boot
 2      501MB   11.5GB  11.0GB  extended
 5      501MB   7500MB  6999MB  logical   ext4
 6      7502MB  11.5GB  3999MB  logical   linux-swap(v1)
```

So far everything looks fine. 

Assuming grub is installed on /dev/sdb, and if you followed that tutorial as i think you did, it will be installed there. You don't look like you have done anything wrong.

It's interesting that the 16GB drive would not boot on both PCs. 

Maybe it's something about the SanDisk Cruzer Edge Disk 16Gb. 
That is also something i have come across in the past. 
Some USB sticks would not boot whereas others would. 
I remember one that had a hidden partition that caused that problem and i think i had to use the manufactures utility to remove it. I can't remember the model though.

Can you boot the 4GB on both PCs and what model is the 4GB if you can ?

Kind regards

---

### Post by samuel15 on 2014-10-19
Hi,

I just noticed that the 4GB one isn't 4GB its 8GB. Sorry my mistake.


Also the 8GB one is the installer one. Just making sure you know.


So are you trying to say, use the 8GB one as the OS and the 16GB one as the installer (or even use an old 2GB one as the installer to avoid problems)?


Finally the 8GB one is a SanDisk Cruser Blade. With it being the same make will it work? I'm not sure

---

### Post by matt_symes on 2014-10-19
Hi

> **samuel15 said:**
> Hi,

I just noticed that the 4GB one isn't 4GB its 8GB. Sorry my mistake.

Also the 8GB one is the installer one. Just making sure you know.


Is the 8GB installer booting correctly in both the Lubuntu PC and the broken PC ? I.E Will the 2 advent PCs boot any of the SanDisks ?

> So are you trying to say, use the 8GB one as the OS and the 16GB one as the installer (or even use an old 2GB one as the installer to avoid problems)?

That may be an idea, however...

> Finally the 8GB one is a SanDisk Cruser Blade. With it being the same make will it work? I'm not sure

...neither am i. It looks like you have done everything right to create the 16GB OS USB Stick.

I'm not sure what to suggest at the moment.

See if others have any idea.

Kind regards

---

### Post by smoliar on 2015-02-14
hi guys,,, i have same problem as this guy,,, but it on second new hdd

---

### Post by oldos2er on 2015-02-14
smoliar, please start a new thread and give as many details about your problem as possible; you'll be much more likely to get help.

---

