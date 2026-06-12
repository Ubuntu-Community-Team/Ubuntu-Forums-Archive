---
title: "Not Detecting Disks 10.10"
date: 2011-04-09
forum: Installation &amp; Upgrades
---

### Post by Peterpuck12 on 2011-04-09
I am attempting to install ubuntu 10.10-alternate-i386 that was burned on a cd. 

Motherboard: SOYO SY-K7ADA v1.0-2AA1
Main Processor: AMD Athlon 1700+
Primary Master: WDC WD800AAJB-00J3A0 0.103E01

The HDD is brand new and hasn't been formated, partitioned, or previously had any other OS on it.  The HDD is recognized in the BIOS.  I am able to get to the Ubuntu Install screen, and proceed to follow through the first eight steps on the install process:

( 1 )Choose language
( 2 )Configure the keyboard
( 3 )Detect and mount CD-ROM
( 4 )Load Debconf preconfiguration file
( 5 )Load installer components from CD
( 6 )Detect network hardware
( 7 )Configure the network
( 8 )Configure the clock

When it gets to the 9th step (Detect disks), I am given this response: 



                          [!] Detect disks

No disk was detected. If you know the name of the driver needed by your disk drive, you can select it from the list.

Driver needed for your disk drive:



-A list of possible drivers are listed in which don't match, except for two, but they don't lead to anywhere beneficial in order to complete the installation process.

At this point, I have no idea how I must proceed.  Any suggestions, comments, guidance, and/or help, would be greatly appreciated. I look forward to hearing from you.  The sooner the better.

---

### Post by Hedgehog1 on 2011-04-09
You need to partition map on the disk.

May I suggest the following installation preparations:

Boot from the LiveCD/LiveUSB, select 'TRY' and then menu to: System >> Administration >> gparted partition manager.

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]


**[SIZE="3"]You can now use the automatic install, or follow the ideas below for a manually controlled install:[/SIZE]**


**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-09
**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-09
**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

**Now when you re-install, select this method:**

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

**And tell the install to use the three partitions this way (You Drive is likely /dev/sda, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]


***The Hedge***

:KS

---

### Post by Peterpuck12 on 2011-04-09
Thanks Hedgehog1.

I had done as you had told me to, and used the Live CD installation version rather than the alternate.  After Ubuntu was preparing to begin the installation process, the screen turned black, and an error message popped up. [Error Message]:


BusyBox V1.15.3 (Ubuntu 1:1.15.3 - 1 Ubuntu5) built-in shell (ash)
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

---

### Post by Hedgehog1 on 2011-04-10
YUCK!!!!  That is an unpleasant surprise!

This error:
> BusyBox V1.15.3 (Ubuntu 1:1.15.3 - 1 Ubuntu5) built-in shell (ash)
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfsis coming from the CD drive, not the hard drive.  

The quickest way past this is to create a LiveUSB and do the install from that (I just did this myself about 4 hours ago!).

Please use **unetbootin** [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") to convert the ISO into a LiveUSB, and then install using that.

***The Hedge***

:KS

---

### Post by Peterpuck12 on 2011-04-10
How large must my usb be in order to proceed?

---

### Post by Hedgehog1 on 2011-04-10
For a LiveUSB, a 1 gig or larger USB stick will work.



***The Hedge***

:KS

---

### Post by Peterpuck12 on 2011-04-11
Good news: I had successfully created a LiveUSB to do the installation.

Bad news: My BIOS is not recognizing the USB as an option to boot from. 
   - I had tried the other options that were presented in the BIOS in order to see if it would potentially boot from the USB, but it was a no go.  Unless I am overlooking a step.

Thanks for the patience.

---

### Post by Peterpuck12 on 2011-04-11
Out of curiosity, do you think it would be beneficial to use a Minimal CD Image? 

Link: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Hedgehog1 on 2011-04-12
I don't think using a different CD image will help. if the PC does not boot from USB, a different CD image wont change that.

However, you are very welcome to try (as a learning experience). if is does not boot, you learn.  If it does boot the a different CD image, then I learn.

The Hedge

:KS

---

### Post by Peterpuck12 on 2011-04-12
> I don't think using a different CD image will help. if the PC does not boot from USB, a different CD image wont change that.

However, you are very welcome to try (as a learning experience). if is does not boot, you learn. If it does boot the a different CD image, then I learn.

Well, I learned from this experience.  It was unable to boot from the LiveUSB or LiveCD with the different CD image.

On another note,

> YUCK!!!! That is an unpleasant surprise!

This error:
Quote:
BusyBox V1.15.3 (Ubuntu 1:1.15.3 - 1 Ubuntu5) built-in shell (ash)
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
is coming from the CD drive, not the hard drive. 

The quickest way past this is to create a LiveUSB and do the install from that (I just did this myself about 4 hours ago!).

Since you had given the quickest way to solve this problem, are there are any other options that I have to go about getting around this?

---

### Post by Dutch70 on 2011-04-12
If you just can't boot from a cd or usb stick. There is a something called PLoP that some people are using.
I don't know anything else about it, but of course you can do a web search.

---

### Post by Hedgehog1 on 2011-04-12
OK - the 'not-the-quickest-way'.

--First---------------------

Please download the ISO again using a Bit Torrent client, and then burn a new CD (or DVD) from the ISO at the very slowest speed. Repeat the install.

--If 'First' fails----------

If the new CD/DVD will still not install, then do this.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

--------------


***The Hedge***

:KS

p.s. The 'Plop' Dutch70 was referring to is here: [http://www.plop.at/]("http://www.plop.at/") It allows booting off a CD, and then jumping to a USB.  However, lets make sure the ISO is clean, first.

---

### Post by Peterpuck12 on 2011-04-13
I was able to get to the desktop via "Try Ubuntu Before the Installation" with the newly created LiveCD that you had requested me to make.  I ran into a problem with the screen getting a bit "funky" on me by, and solved it by using the kernel nomodeset before proceeding to "Try Ubuntu Before the Installation".  

At this point I went back to your initial posting about opening GParted Partition Editor, and continue with that path.  Another surprise occurred once opening GParted Partition Editor.  My hdd isn't being detected.  Next, I downloaded Boot Info Script, and got this as the result:

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```I don't know if this helps.  I also double checked to see if everything is plugged in correctly, and it is.  The BIOS confirms that it recognises the hdd.  So far, there has been progress, and I appreciate your help thus far.  I'm sure its something simple that I am overlooking.

---

### Post by Hedgehog1 on 2011-04-14
I want to be sure I understand.

You are seeing the 'no devices detected' situation:

[IMG]http://img193.imageshack.us/img193/9980/harddrivemissing.png[/IMG]

And not the 'unallocated' situation:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]


Sorry to drag this out - but I don't want to lead you astray...


***The Hedge***

:KS

---

### Post by Peterpuck12 on 2011-04-14
Yes, I am not seeing the 'no devices detected' situation.  The first of the two options you had presented to me.  Sorry, I should have been more descriptive.  No worries about dragging it out. I agree to better communication even if it takes the longer path, otherwise shortcuts could lead to more dead ends.

---

### Post by Hedgehog1 on 2011-04-14
OK - that picture was from a system whose drive was failing.  Between the beginning of the  thread and the 15th post, it stopped showing up in BIOS, too.

However, sometimes the issue is BIOS setup for the drive.  There are a number of behavior options (depending on your BIOS complexity).  Please write down the current settings before changing them for the drive, and then give the other options a try.

Also, moving the drive cable to a different SATA plug can solve this.  If your Mother Board supports RAID on some SATA ports, plug this drive into a non-RAID SATA port.

If it is an IDE/PATA drive, make sure it is set to 'master' and not 'slave'.

It can take a bit of fooling to find the right combination.  Hopefully the drive itself is fine.


***The Hedge***

:KS

---

### Post by Peterpuck12 on 2012-09-05
1 year and 5 months later :)  Due to priorities and other responsibilities, I have been unable to continue the solving of this dilemma until now.  Instead of  installing Ubuntu 10.10, I am attempting 12.04.  Unfortunately, the same problem still occurs.

I wrote down the current settings before changing them for the drive, and gave the other options a try.  To no avail, I was unable to complete this task due to my inability of knowing where to start nor understand most of the options and their effects once changed.

Also, I changed the drive cable to a different SATA plug and confirmed that the drive is set to 'master'.

As for the BIOS settings, I wrote down every one, and its options.  I have it listed below to hopefully reveal a simple solution to resolve this.

Note: Black represents specs, Red are the current settings, and Blue are the other options.



```


CMOS Setup Utility - Copyright (c) 1984-2001 Award Software



[COLOR="Blue"]-SOYO COMBO Feature
 -Auto Detect DIMM/PCI Clk[/COLOR]
  [COLOR="Red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled[/COLOR]
 [COLOR="Blue"]-Spread Spectrum[/COLOR]
  [COLOR="Red"]-Disabled[/COLOR]
  [COLOR="Blue"]-Enabled[/COLOR]
 [COLOR="blue"]-CPU HOST/SDRAM/PCI Clock[/COLOR]
  [COLOR="red"]-Default[/COLOR]
  [COLOR="blue"]-100/100/33MHz
  -101/101/33MHz
  -102/102/34MHz
  -103/103/34MHz
  -105/105/35MHz
  -107/107/35MHz
  -110/110/36MHz
  -133/133/33MHz
  -136/136/34MHz
  -137/137/34MHz
  -140/140/35MHz
  -143/143/35MHz
  -146/146/37MHz
 -System Performance[/COLOR]
  [COLOR="Red"]-Normal[/COLOR]
  [COLOR="blue"]-Maximum
 -Quick Power On Self Test[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -First Boot Device[/COLOR]
  [COLOR="red"]-HDD-0[/COLOR]
  [COLOR="blue"]-Floppy
  -LS120
  -SCSI
  -CDROM
  -HDD-1
  -HDD-2
  -HDD-3
  -ZIP100
  -LAN
  -Disabled
 -Second Boot Device[/COLOR]
  [COLOR="red"]-CDROM[/COLOR]
  [COLOR="blue"]-Floppy
  -LS120
  -SCSI
  -HDD-0
  -HDD-1
  -HDD-2
  -HDD-3
  -ZIP100
  -LAN
 -Third Boot Device[/COLOR]
  [COLOR="red"]-SCSI[/COLOR]
 [COLOR="blue"] -CDROM
  -Floppy
  -LS120
  -HDD-0
  -HDD-1
  -HDD-2
  -HDD-3
  -ZIP100
  -LAN
 -Boot Other Device[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-SCSI
  -CDROM
  -Floppy
  -LS120
  -HDD-0
  -HDD-1
  -HDD-2
  -HDD-3
  -ZIP100
  -LAN
 -ALI On-Chip Audio[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -POWER ON Function[/COLOR]
  [COLOR="red"]-BUTTON ONLY[/COLOR]
 [COLOR="blue"]-Password
  -Hot KEY
  -Mouse Left
  -Mouse Right
  -Keyboard 98
-Standard CMOS Features
 -IDE Primary Master
  -IDE HDD Auto-Detection[/COLOR]
   [COLOR="red"]-Press Enter[/COLOR]
  [COLOR="blue"]-IDE Primary Master - WDCWD800AAJB-00J3A0[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-None
   -Manual
  -Access Mode[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-CHS
   -LBA
   -Large[/COLOR]

     Capacity      80GB
     Cylinder      38309
     Head          16
     Precomp       0
     Landing Zone  38308
     Sector        255

 [COLOR="blue"]-IDE Primary Slave - None
  -IDE HDD Auto Detection[/COLOR]
   [COLOR="red"]-Press Enter[/COLOR]
  [COLOR="blue"]-IDE Primary Slave[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-None
   -Manual
  -Access Mode[/COLOR]
   [COLOR="red"]-Auto[/COLOR] 
   [COLOR="blue"]-CHS
   -LBA
   -Large[/COLOR]

     Capacity      0 MB
     Cylinder      0
     Head          0
     Precomp       0
     Landing Zone  0
     Sector        0

 [COLOR="blue"]-IDE Secondary Master - ATAPI 52x CDROM
  -IDE HDD Auto-Detection[/COLOR]
   [COLOR="red"]-Press Enter[/COLOR]
  [COLOR="blue"]-IDE Secondary Master[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-None
   -Manual
  -Access Mode[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-CHS
   -LBA
   -Large[/COLOR]

     Capacity      0 MB
     Cylinder      0
     Head          0
     Precomp       0
     Landing Zone  0
     Sector        0

 [COLOR="blue"]-IDE Secondary Slave - None[/COLOR]
  [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-None
   -Manual
  -Access Mode[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-CHS
   -LBA
   -Large[/COLOR]

     Capacity      0 MB
     Cylinder      0
     Head          0
     Precomp       0
     Landing Zone  0
     Sector        0

 [COLOR="blue"]-Drive A[/COLOR]
  [COLOR="red"]-1.44M, 3.5  in.[/COLOR]
  [COLOR="blue"]-None
  -360K, 5.25 in.
  -1.2M, 5.25 in.
  -720K, 3.5 in
  -2.88M, 3.5 in.
 -Drive B[/COLOR]
  [COLOR="red"]-None[/COLOR]
  [COLOR="blue"]-360K, 5.25 in.
  -1.2M, 5.25 in.
  -720K, 3.5 in
  -1.44M, 3.5 in.
  -2.88M, 3.5 in.
 -Floppy 3 Mode Support[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"][COLOR="blue"]-Drive A
  -Drive B
  -Both
 -Video[/COLOR][/COLOR]
  [COLOR="red"]-EGA/VGA[/COLOR]
  [COLOR="blue"]-CGA 40
  -CGA 80
  -MONO
 -Halt On[/COLOR]
  [COLOR="red"]-All Errors[/COLOR]
  [COLOR="blue"]-No Errors
  -All, But Keyboard
  -All, But Diskette
  -All, But Disk/Key[/COLOR]

    Base Memory      640K
    Extended Memory  1047552K
    Total Memory     1048576K

[COLOR="blue"]-Advanced BIOS Features
 -Virus Warning[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -CPU Internal Cache[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -External Cache[/COLOR]
  [COLOR="red"]-Enabled[/COLOR] 
  [COLOR="blue"]-Disabled
 -Swap Floppy Drive[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -Boot Up Floppy Seek[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Boot Up NumLock Status[/COLOR]
  [COLOR="red"]-On[/COLOR]
  [COLOR="blue"]-Off
 -Boot Up System Speed[/COLOR]
  [COLOR="red"]-High[/COLOR]
  [COLOR="blue"]-Low
 -Gate A20 Option[/COLOR]
  [COLOR="red"]-Fast[/COLOR]
  [COLOR="blue"]-Normal
 -Typematic Rate Setting[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled[/COLOR]

x Typematic Rate (Chars/Sec)  6
x Typematic Delay (MSec)      250

 [COLOR="blue"]-Security Option[/COLOR]
  [COLOR="red"]-Setup[/COLOR]
  [COLOR="blue"]-System
 -OS Select For DRAM > 64MB[/COLOR]
  [COLOR="red"]-Non-OS2[/COLOR]
  [COLOR="blue"]-OS2
 -Report No FDD For WIN95[/COLOR]
  [COLOR="red"]-No[/COLOR]
  [COLOR="blue"]-Yes
 -Video BIOS Shadow[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -EPA LOGO SELECT[/COLOR]
  [COLOR="red"]-LOGO-0[/COLOR]
  [COLOR="blue"]-LOGO-1
 -Small Logo (EPA) Show[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Advanced Chipset Feature
  -DRAM CAS Select[/COLOR]
  [COLOR="red"]-2.5[/COLOR]
  [COLOR="blue"]-Auto (By SPD)
  -2
 -Dram performance[/COLOR]
  [COLOR="red"]-Normal[/COLOR]
 [COLOR="blue"] -Auto (By SPD)
  -Failsafe
  -Slow
  -Fast
  -Ultra
  -Ultra 2
 -At Bus Clock[/COLOR]
  [COLOR="red"]-CLK2/4[/COLOR]
 [COLOR="blue"] -7.16 MHz
  -CLK2/2
  -CLK2/3
  -CLK2/5
  -CLK2/6
 -System BIOS Cacheable[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -AGP Aperture Size[/COLOR]
  [COLOR="red"]-128MB[/COLOR]
  [COLOR="blue"]-32MB
  -64MB
  -256MB
 -AGP Delay Offset[/COLOR]
  [COLOR="red"]-Auto[/COLOR]
 [COLOR="blue"] -1
  -2
  -3
  -4
  -5
  -6
  -7
  - -1
  - -2
  - -3
  - -4
  - -5 
  - -6
  - -7
 -AGP Driving Strength
[/COLOR]  [COLOR="red"]-Auto[/COLOR]
  [COLOR="blue"]-Low
  -Mid
  -High
 -I/O Recovery Period[/COLOR]
  [COLOR="red"]-1us[/COLOR]
  [COLOR="blue"]-2us
  -3us
 -ALI On-Chip GamePort[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Passive Release[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
-Integrated Peripherals
 -On-Chip Primary IDE[/COLOR]
   [COLOR="red"]-Enabled[/COLOR]
   [COLOR="blue"]-Disabled
  -Master PIO[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-Mode 0
   -Mode 1
   -Mode 2
   -Mode 3
   -Mode 4
  -Slave PIO[/COLOR]
   [COLOR="red"]-Auto [/COLOR]
   [COLOR="blue"]-Mode 0
   -Mode 1
   -Mode 2
   -Mode 3
   -Mode 4
  -Master Ultra DMA[/COLOR]
   [COLOR="red"]-Auto[/COLOR] 
   [COLOR="blue"]-Disabled
  -Slave Ultra DMA[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-Disabled
 -On-Chip Secondary IDE[/COLOR]
   [COLOR="red"]-Enabled[/COLOR]
   [COLOR="blue"]-Disabled
  -Master PIO[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-Mode 0
   -Mode 1
   -Mode 2
   -Mode 3
   -Mode 4
  -Slave PIO[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
  [COLOR="blue"] -Mode 0
   -Mode 1
   -Mode 2
   -Mode 3
   -Mode 4
  -Master Ultra DMA[/COLOR]
   [COLOR="red"]-Auto[/COLOR] 
   [COLOR="blue"]-Disabled
  -Slave Ultra DMA[/COLOR]
   [COLOR="red"]-Auto[/COLOR]
   [COLOR="blue"]-Disabled
 -On-Chip USB Controller[/COLOR]
   [COLOR="red"]-Enabled[/COLOR]
   [COLOR="blue"]-Disabled
  -USB Keyboard Support[/COLOR]
   [COLOR="red"]-Disabled[/COLOR]
   [COLOR="blue"]-Enabled
 -Init Display First[/COLOR]
  [COLOR="red"]-AGP[/COLOR]
  [COLOR="blue"]-PCI Slot
 -IDE HDD Block Mode[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Onboard FDC Controller[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Onboard Serial Port 1[/COLOR]
  [COLOR="red"]-3F8/IRQ4[/COLOR]
  [COLOR="blue"]-Disabled
  -2F8/IRQ3
  -3E8/IRQ4
  -2E8/IRQ3
 -Onboard Serial Port 2[/COLOR]
  [COLOR="red"]-2F8/IRQ3[/COLOR]
  [COLOR="blue"]-Disabled
  -3F8/IRQ4
  -3E8/IRQ4
  -2E8/IRQ3
 -Onboard Serial Port 3[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-2F8/IRQ3
  -3F8/IRQ4
  -3E8/IRQ4
  -2E8/IRQ3
  -3E8/IRQ10
  -2E8/IRQ11[/COLOR]

x UART Mode Select      IrDA
x RxD, TxD Active       Hi, Lo
x IR Duplex Mode        Half
x Fast IR Mode Use DMA  1

 [COLOR="blue"]-Onboard Parallel Port[/COLOR]
  [COLOR="red"]-378/IRQ7[/COLOR]
  [COLOR="blue"]-Disabled
  -278/IRQ5
  -3BC/IRQ7
 -Parallel Port Mode[/COLOR]
  [COLOR="red"]-SPP[/COLOR]
  [COLOR="blue"]-EPP1.9
  -ECP
  -ECP+EPP1.9
  -EPP1.7
  -ECP+EPP1.7[/COLOR]

x ECP Mode Use DMA

[COLOR="blue"]-Power Management Setup
 -ACPI Suspend Type[/COLOR]
  [COLOR="red"]-S1 (POS)[/COLOR]
  [COLOR="blue"]-S3 (STR)
 -Power Management[/COLOR]
  [COLOR="red"]-User Define[/COLOR]
  [COLOR="blue"]-Min Saving
  -Max Saving
 -PM Control by APM[/COLOR]
  [COLOR="red"]-No[/COLOR]
  [COLOR="blue"]-Yes
 -MODEM Use IRQ[/COLOR]
  [COLOR="red"]-3[/COLOR]
[COLOR="blue"]  -NA
  -4
  -5
  -7
  -9
  -10
  -11
 -Video Off In Suspend[/COLOR]
  [COLOR="red"]-Yes[/COLOR]
  [COLOR="blue"]-No
 -Video Off Method[/COLOR]
  [COLOR="red"]-DPMS[/COLOR]
  [COLOR="blue"]-Blank Screen
  -V/H SYNC+Blank[/COLOR]

PM Timers

 [COLOR="blue"]-HDD Power Down[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
 [COLOR="blue"] -1 min
  -2 min
  -3 min
  -4 min
  -5 min
  -6 min
  -7 min
  -8 min
  -9 min
  -10 min
  -11 min
  -12 min
  -13 min
  -14 min
  -15 min
 -Suspend Mode[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
 [COLOR="blue"] -1 min
  -2 min
  -4 min
  -8 min 
  -12 min
  -20 min
  -30 min
  -40 min
  -1 Hour[/COLOR]

***Power On/WakeUp Functions***

 [COLOR="blue"]-Soft-Off by PWR-BTTN[/COLOR]
  [COLOR="red"]-Instant-Off[/COLOR]
  [COLOR="blue"]-Delay 4 sec.
 -WakeUp\PowerOn by PCI Card[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -WakeUp\PowerOn by Ring[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -Resume by Alarm[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled[/COLOR]

***Suspend Break Events***

 [COLOR="blue"]-IRQ[1] (Keyboard)[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -IRQ[3][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[4][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[5][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[6] (Floppy Disk)[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -IRQ[7][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[8] (RTC)[/COLOR]
  [COLOR="red"]-Disable[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[9][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[10][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[11][/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -IRQ[12] (PS2 Mouse)[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -IRQ[14] (Primary IDE)[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -IRQ[15] (Secondary IDE)[/COLOR]
  [COLOR="red"]-Disabled[/COLOR] 
  [COLOR="blue"]-Enabled
-PnP/PCI Configurations
 -PNP OS Installed[/COLOR]
  [COLOR="red"]-No[/COLOR]
  [COLOR="blue"]-Yes
 -Reset Configuration Data[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -Resources Controlled By[/COLOR]
  [COLOR="red"]-Auto (ESCD)[/COLOR]
  [COLOR="blue"]-Manual
 -PCI/VGA Palette Snoop[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-Enabled
 -Assign IRQ For VGA[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -Assign IRQ For USB[/COLOR]
  [COLOR="red"]-Enabled[/COLOR]
  [COLOR="blue"]-Disabled
 -PCI IRQ Activated By[/COLOR]
  [COLOR="red"]-Level[/COLOR]
 [COLOR="blue"] -Edge
-PC Health Status
 -CPU Warning Temperature[/COLOR]
  [COLOR="red"]-Disabled[/COLOR]
  [COLOR="blue"]-50C/122F
  -53C/127F
  -56C/133F
  -60C/140F
  -63C/145F
  -66C/151F
  -70C/158F[/COLOR]

Current SYS Temperature  40C/104F
Current CPU Temperature  42C/107F
Current CPUFAN Speed     ~5000 RPM
Current CHAFAN Speed     0 RPM

VCore                    1.71V
+3.3V                    3.39V
+5V                      4.99V
+12V                     12.33V

 [COLOR="blue"]-Shutdown Temperature[/COLOR]
  [COLOR="red"]-75C/167F[/COLOR]
  [COLOR="Blue"]-60C/140F
  -65C/149F
  -70C/158F[/COLOR]

```

---

