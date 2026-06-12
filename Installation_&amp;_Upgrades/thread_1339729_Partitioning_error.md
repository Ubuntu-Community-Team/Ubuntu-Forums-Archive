---
title: "Partitioning error"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by earlingy on 2009-11-27
I have an ASUS eee pc.  It has a 16gb SSD.  It came with xp, and I ran kubuntu and xp together on it for a while.  Recently it started giving me a disk read error message and wouldn't boot, so I made a linux boot flash drive, and am attempting to install ubuntu with it.  It starts the install no problem, but then at 5% it gives me this message:
Do you want to resume partitioning?
The attempt to mount a file system with type ext4 in SCSI2 (0,0,0), partition #1 (sda) failed.  You may resume partitioning from the partitioning menu.

When I then click continue, it takes me to the partitioning menu.  It says, "This computer has no operating systems on it." 
And it shows 14.4GB of /dev/sda1 and 690.3MB or swap (/dev/sda5)
I then have the choice, "Install them side by side, choosing between them each startup"
or "Erase and use the entire disk"

Well, I don't even care about saving any files I had on windows xp.  I already wanted to reformat the entire laptop and run just ubuntu.  So, I want to choose "Erase and the use the entire disk", but that is what I already had selected and it will do the same install and give me the same message, and send me back to the same partitioning menu if I select "Erase and use the entire disk" I want no other partitions to select from at boot, I want to boot the computer and it goes straight to ubuntu.
What do I do?

---

### Post by earlingy on 2010-01-07
K, I clicked around and finally it would get further into the installation, but halfway in, tell me installation failed due to hard drive error.  So I bought a new hard drive and installed that.  I again attempted to install Ubuntu.  The first time through, I chose "Erase and use the entire disk"
Well, it gave me the same error message as the first time in the last post.  But, now when I try to return to the partitioner, it freezes up at 70%, saying "Detecting File Systems."  No matter how long I give it, it will go no further.
I also reformatted my usb linux bootable flash drive, and tried Netbook Remix.  It still will not get past 70%.
Any ideas?
Thanks!

---

### Post by earlingy on 2010-01-08
Couple other live linux OSs will work, but haven't been able to get any to install to the hard drive.  Fedora would open up the partitioner, but still wouldn't finish an install.

---

### Post by earlingy on 2010-01-09
Alright, I could get the partitioner in fedora to run- I deleted all the partitions in there, then used a UNR 9.04 usb drive made from a .img rather than a .iso, the partitioner would start up then in UNR 9.04 installer- I got it to work using the choice "Use the free space" leaving sda1 partition as an unused 200MB.  The install completed and worked fine, until I tried to update to UNR 9.10.  Halfway through, it froze up, and wouldn't boot.  I repeated the same process with fedora, but this time it didn't give the the "Use free space" choice.  Only erase and use the whole hard drive or set partitions manually.  Erase and use the whole drive didn't work, same issue as the original Failed to make partition.  WELL....I fiddled around with set partitions manually although I don't know how to do that really...and figured out that it will set up partitions anywhere except sda1.  If I leave sda1 unused, it will set up ext3 file systems just fine anywhere else.  I would really appreciate any input from someone who knows more about partitioning and different sda#'s.
Thanks

---

### Post by darkod on 2010-01-09
Running from live USB can you execute in terminal:
sudo fdisk -l

and post the results here. It will show your drives/partitions. I can give you few pointers once I know what you have.

---

### Post by earlingy on 2010-01-10
Darko- thanks so much for helping out!
Does this look right?

sudo fdisk -l

Disk /dev/sdb: 3951 MB, 3951034368 bytes
122 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 7564 * 512 = 3872768 bytes
Disk identifier: 0xb0bcd68e

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      426146      458759   123339962   78  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(518, 102, 15) logical=(426145, 96, 50)
Partition 1 has different physical/logical endings:
     phys=(743, 0, 62) logical=(458758, 19, 15)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       57228      159778   387841909+  10  OPUS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(205, 7, 0) logical=(57227, 98, 14)
Partition 2 has different physical/logical endings:
     phys=(920, 235, 50) logical=(159777, 27, 34)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      247166      500899   959615034   8b  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(260, 125, 54) logical=(247165, 104, 56)
Partition 3 has different physical/logical endings:
     phys=(893, 46, 60) logical=(500898, 2, 35)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?      283354      284455     4161546+   a  OS/2 Boot Manager
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(269, 111, 50) logical=(283353, 116, 61)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(284454, 38, 25)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by darkod on 2010-01-10
Not looking right at all. First of all, it's showing only the 4GB disk which is named /dev/sdb. The 16GB should probably be /dev/sda but it's not even shown. Hmmm... :(
Second, even for /dev/sdb the partitions list is full of errors as you can see.

If you don't have any data to save on the 4GB disk, while you are booted with the ubuntu usb, Try Ubuntu, open Gparted (System-Administration) and delete all partitions on /dev/sdb.
Note that initially Gparted only schedules your commands, in case you change your mind. After you're done deleting the partitions, you have to click the big green tick mark button in the Gparted toolbar to execute your commands. Only then they will be deleted.

Maybe that can help but I'm still confused about the 16GB disk and that would have been better to use because of the larger size.

PS. Are you sure the 16GB disk is not somehow disabled in BIOS and not showing because of that or something similar?

---

### Post by gqqser on 2010-01-12
I am having the exact same problem loading ubuntu remix 9.10 on my Acer AspireOne. here are the results from my drive. Sorry if I am just jumping in here but I have exhausted every avenue and I have been dealing with this for 4 days now.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders
Units = cylinders of 529 * 512 = 270848 bytes
Disk identifier: 0x418d1131

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16       14805     3911744    b  W95 FAT32

Disk /dev/mmcblk0: 8017 MB, 8017936384 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005b957

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         926     7438063+  83  Linux
/dev/mmcblk0p2             927         974      385560    5  Extended
/dev/mmcblk0p5             927         974      385528+  82  Linux swap / Solaris

any help would surely be appreciated.

---

### Post by darkod on 2010-01-12
> **gqqser said:**
> I am having the exact same problem loading ubuntu remix 9.10 on my Acer AspireOne. here are the results from my drive. Sorry if I am just jumping in here but I have exhausted every avenue and I have been dealing with this for 4 days now.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders
Units = cylinders of 529 * 512 = 270848 bytes
Disk identifier: 0x418d1131

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          16       14805     3911744    b  W95 FAT32

Disk /dev/mmcblk0: 8017 MB, 8017936384 bytes
255 heads, 63 sectors/track, 974 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005b957

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           1         926     7438063+  83  Linux
/dev/mmcblk0p2             927         974      385560    5  Extended
/dev/mmcblk0p5             927         974      385528+  82  Linux swap / Solaris

any help would surely be appreciated.

It seems you have ubuntu installed on /dev/mmcblk0. What is not working for you exactly?
And also you have device /dev/sdb of 4GB but no 16GB device (maybe that should be 16GB). I'm going to search for specs of these AspireOne. I'm confused why that 16GB disk is not showing.

---

### Post by gqqser on 2010-01-12
I boot off the memory stick and everything starts fine. I go to install off the memory stick by clicking on "install Ubuntu-Netbook-Remix 9.10" app on the desktop under favorites.

It opens the app with a welcome screen and asks if I want English as my language.

after answering "yes" I click forward and then it asks what time zone.

I then click forward again

at this point it asks about my keyboard, I type some jibberish in the test box because the one I want is already selected, I then click forward (step 3of 6 of the installation)

Then it asks, "The installer has detected that the following disks have mounted partitions:

/dev/mmcblk0

"Do you want the installer to try to unmount the partitions on these disks before continuing?

I have selected both in the previous 8 times I have tried to install this. but for arguments sake, I click on "yes"

A window appears "Starting up the partitioner" dialog box, the animated progress bar goes to 70% and stays there...under that it says Detecting file systems on the same dialog box.

thats it...man I really appreciate you looking at this for me.

---

### Post by darkod on 2010-01-12
> **gqqser said:**
> I boot off the memory stick and everything starts fine. I go to install off the memory stick by clicking on "install Ubuntu-Netbook-Remix 9.10" app on the desktop under favorites.

It opens the app with a welcome screen and asks if I want English as my language.

after answering "yes" I click forward and then it asks what time zone.

I then click forward again

at this point it asks about my keyboard, I type some jibberish in the test box because the one I want is already selected, I then click forward (step 3of 6 of the installation)

Then it asks, "The installer has detected that the following disks have mounted partitions:

/dev/mmcblk0

"Do you want the installer to try to unmount the partitions on these disks before continuing?

I have selected both in the previous 8 times I have tried to install this. but for arguments sake, I click on "yes"

A window appears "Starting up the partitioner" dialog box, the animated progress bar goes to 70% and stays there...under that it says Detecting file systems on the same dialog box.

thats it...man I really appreciate you looking at this for me.

OK, since I don't know what hardware you've got, and there are too many versions of Aspire One, please break it down for me. You already saw your fdisk results.
1. What is the 4GB device named /dev/sdb? Is that the bootable usb stick with ubuntu install files on it?
2. The other shown device is 8GB what looks like MMC card. Is this where you want ubuntu installed to?
3. Do you have any other hdd (ssd) except the mentioned above? If those devices are a usb stick and a MMC card, you need to have at least a hdd or ssd inside right?

---

### Post by gqqser on 2010-01-12
[LEFT]**Processor & Chipset**[/LEFT]
   [LEFT]- Intel® Atom™ processor N270 (1.60 GHz, 533 MHz FSB, 512 KB L2 cache)
- Mobile Intel® 945GSE Express Chipset (DDR2 400/533 MHz)
- Mobile Intel® 82801GBM Chipset[/LEFT]
     [LEFT]**Operating System**[/LEFT]
   [LEFT]- Linpus™ Linux® Lite version
- Windows XP® Home[/LEFT]
     [LEFT]**Memory**[/LEFT]
   [LEFT]- Single channel with onboard SDRAM and one soDIMM slot
• DDR2 533 MHz SDRAM memory interface design
• Onboard SDRAM: 512 MB
- soDIMM slot: Supports 512 MB/1 GB soDIMMs for total system memory of up to 1.5 GB5[/LEFT]
     [LEFT]**Storage**[/LEFT]
   [LEFT]- NAND flash module or hard disk drive for internal storage7
- NAND flash module: 8 GB
- Hard disk drive7: 2.5&#8243; 9.5 mm 120GB
- Storage expansion: SD™ Card reader
- Multi-in-1 card reader: Supporting Secure Digital™ (SD) Card, MultiMediaCard (MMC), Reduced-Size Multimedia Card (RS-MMC), Memory Stick® (MS), Memory Stick PRO™ (MS PRO), xD-Picture Card™ (xD)
- Supporting storage cards with adapter: miniSD™, microSD™, Memory Stick Duo™, Memory Stick PRO Duo™[/LEFT]
     [LEFT]**Display**[/LEFT]
   [LEFT]- 8.9&#8243; WSVGA high-brightness (typical 180-nit) Acer CrystalBrite™ TFT LCD, 1024 x 600 pixel resolution
• LED backlight
• 262,000 colors supported[/LEFT]
     [LEFT]**Multimedia**[/LEFT]
   [LEFT]- High-definition audio support
- Two built-in stereo speakers
- MS-Sound compatible
- Built-in digital microphone[/LEFT]
     [LEFT]**Communication**[/LEFT]
   [LEFT]- Integrated Acer Crystal Eye webcam, supporting 0.3 megapixel resolution
- WLAN2: Acer InviLink™ 802.11b/g Wi-Fi CERTIFIED® network connection, supporting Acer SignalUp™ wireless technology,
- LAN: 10/100 Mbps Fast Ethernet
- WWAN8: UMTS/HSPA (High-Speed Packet Access) at 850/1900/2100 MHz and quad-band GSM/GPRS/EDGE (850/900/1800/1900 MHz), upgradeable to 7.2 Mb/s HSDPA and 2 Mb/s HSUPA (for 3G models)
- Supports receiver diversity and equalizes at 2100 MHz
- Acer InviLink™ 802.11b/g Wi-Fi CERTIFIED® network connection, supporting Acer SignalUp™ wireless technology2[/LEFT]
     [LEFT]**I/O Interfaces**[/LEFT]
   [LEFT]- Multi-in-1 card reader
- SD™ Card reader for storage expansion
- Three USB 2.0 ports
- External display (VGA) port
- Headphone/speaker/line-out jack
- Microphone-in jack
- Ethernet (RJ-45) port
- DC-in jack for AC adapter[/LEFT]
     [LEFT]**Power supply and Battery**[/LEFT]
   [LEFT]- 30 W adapter with power cord
- 24 W 2200 mAh 3-cell Li-ion battery pack
- 57 W 2600 mAh 6-cell Li-ion battery pack
- 3-hour battery life for SKUS with NAND flash module and 3-cell battery pack
- 7-hour battery life for SKUS with NAND flash module and 6-cell battery pack[/LEFT]
     [LEFT]**Keyboard & Special Controls**[/LEFT]
   [LEFT]- 84-key keyboard with 1.6 mm (minimum) key travel
- Touchpad pointing device with two buttons
- 12 function keys, four cursor keys, one Windows® key for Windows® XP Home or one Home key for Linpus™
- Linux® Lite version, hotkey controls, embedded numeric keypad, international language support
- Power button with LED
- Easy-access switches with LED: WLAN, WWAN1[/LEFT]
     [LEFT]**Weight and Dimensions**[/LEFT]
   [LEFT]- 249 (W) x 170 (D) x 29 (H) mm (9.8 x 6.7 x 1.14 inches) for SKUs with NAND flash module and 3-cell battery pack
- 249 (W) x 195 (D) x 36 (H) mm (9.8 x 6.7 x 1.42 inches) for SKUs with hard disk drive and 6-cell battery pack
- 995 g (2.19 lbs.) for SKUs with NAND flash module and 3-cell battery pack
- 1.26 kg (2.78 lbs.) for SKUs with hard disk drive and 6-cell battery pack
 [/LEFT]
     [LEFT][B]Software
(Optional)[/B][/LEFT]
   [LEFT]- Linpus™ Linux® Lite version
• OpenOffice 2.3
• Aspire one Mail
• Messenger
- Windows XP® Home
• Acer eRecovery Management
• Acer Launch Manager
• Adobe® Reader®
• McAfee® Internet Security Suite
- Microsoft® Office Trial 2007[/LEFT]

---

### Post by gqqser on 2010-01-12
OK, since I don't know what hardware you've got, and there are too many versions of Aspire One, please break it down for me. You already saw your fdisk results.
1. What is the 4GB device named /dev/sdb? Is that the bootable usb stick with ubuntu install files on it?
2. The other shown device is 8GB what looks like MMC card. Is this where you want ubuntu installed to?
3. Do you have any other hdd (ssd) except the mentioned above? If those devices are a usb stick and a MMC card, you need to have at least a hdd or ssd inside right?[/QUOTE]

1.I believe it is looking at the memory stick. 
2. I believe this to be hard drive
3. no, the 8gig is the hdd I believe

---

### Post by darkod on 2010-01-12
So, you have the 8GB NAND storage and not the 120GB hdd right? We shouldn't be surprised that we are not seeing the 120GB hdd reported by fdisk?

The partitions on the 8GB device look like ubuntu but if the process stalled at 70% it doesn't mean it will work.
I guess you tried lots of things, but just to make sure, can you try the following:
Boot with the stick, Install Ubuntu option, and in step 4 tell it to use the Erase and use whole disk option and in the drop down list select your 8GB device (if not selected by default). See if the installer will return an error or stop again.
Hopefully, it won't.
Note: That option will erase your 8GB device but since your current install is not working I guess you have no files that you need to save from it.

---

### Post by gqqser on 2010-01-12
So, you have the 8GB NAND storage and not the 120GB hdd right? We shouldn't be surprised that we are not seeing the 120GB hdd reported by fdisk?

The partitions on the 8GB device look like ubuntu but if the process stalled at 70% it doesn't mean it will work.
I guess you tried lots of things, but just to make sure, can you try the following:
Boot with the stick, Install Ubuntu option, [COLOR=Red]and in step 4 tell it to use the Erase and use whole disk option and in the drop down list select your 8GB device (if not selected by default). See if the installer will return an error or stop again.[/COLOR]
Hopefully, it won't.
Note: That option will erase your 8GB device but since your current install is not working I guess you have no files that you need to save from it.[/QUOTE]

I cannot get past step 3 in the process...here is something, there is an OEM install prior to entering the GUI. I selected that and had no better luck. I sends me to terminal stating "gave up waiting for root device"

---

### Post by darkod on 2010-01-12
I don't understand which install prior to entering the GUI. You have selected in BIOS to boot from the 4GB usb stick right? And then by selecting Install Ubuntu option, the installer should start, ignoring any OS existing on the 8GB device.
Just for reference, the screenshots of the installer are:
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

I have no idea why you wouldn't be able to proceed from step 3. If that keeps happening I don't know what to suggest... :(
Look what the screenshots are and give it another try.

---

### Post by gqqser on 2010-01-12
Alright...just so you can sleep tonight, haha,  I went back into BIOS and reset the order of the boot sequence...for some reason, it is not seeing the hard drive at bootup...it tries to load from a network drive as that is next in the bootup list. If I change that to USB then it sees the memory stick and boots from that.

I went into Disk utility under the Administration > palimsest Disk Utility in the GUI and what I found was the 8 gig drive is listed 3 times

Look at the attachment...I sent a screenshot
[IMG]file:///home/gary/Desktop/Screenshot.png[/IMG]

---

### Post by darkod on 2010-01-12
It's not listed three times.
1. You have 8GB SD memory card. Is this the memory stick you are referring to?
2. You have 8GB SSD hard disk.
3. You have 4GB usb stick.

I'm still not sure what are you trying to do. Is that 4GB usb stick bootable with the ubunru install files on it? That's how you are trying to install? If that is so, making the USB first in boot order allows you to boot from the stick and start the install process?

Not being able to boot from the 8GB SSD might be a problem. But at the moment maybe you have no bootloader there to boot from. You can see in the screenshot that the first partition on the 8GB SSD says "unrecognized".

Also, if the 8GB SD memory card is just for space expansion, remove it while trying to sort out the ubuntu installation. It just creates confusion.

So, if I've got it right:
1. Remove the SD memory card.
2. Boot from your usb stick and select Install Ubuntu option.
3. Install it on the 8GB SSD hard drive you've got, using Erase and use whole disk option.

When that finishes (hopefully without errors), remove the usb stick and reboot. No SD memory card and no usb stick connected. You should be able to boot your ubuntu installed on the 8GB SSD.

---

### Post by gqqser on 2010-01-13
First off...let me say that a picture is worth a thousand words.

second...Let me also say DARKOD ROCKS!!!!!!!!!

Third...Do not ever load or attempt to load an operating system on a computer for your 22 year old daughter that you have no prior knowledge of.

Fourth... Did I say DARKOD ROCKS!!!!

Thank you so much for hanging in there with me...also, for everyone else, you CANNOT install the operating system on an ACER, Aspire One netbook with the SSD card in the slot!!!

Once I removed the card...which I had no idea she even owned a SSD card....it fired right up the way it was suppossed to...

The weird thing was the boot sequence in BIOS didn't even include the SSD but it kept trying to boot from it...the long and short of this exercise...NO SSD while installing operating system and....

LISTEN TO DARKOD!

Thank You so much!

---

### Post by darkod on 2010-01-13
Thank you very much for the kind words. :oops:

Just a small correction. I believe it was SD card (Secure Digital memory card), it's not called SSD. SSD is for the new generation Solid State Drives, it should not be confused with SD memory card like you use in your digital camera.

You actually do have 8GB SSD drive inside your netbook, but the SD card is different device.

Anyway, glad everything is working now. Once you put the SD card back I think you will have to format it because it seemed to me one of the ubuntu installs went there by mistake. Just hope you didn't delete any photos on it. :) Or you're in trouble. :)

If you leave the card as it is, it might try to boot from it again. If I got it right. So you would need to format it but first try to check what's on it. Cheers.

---

### Post by earlingy on 2010-01-15
So... /endthreadjack/

My computer is an ASUS Eee PC 900. The original drive was a 16GB solid state drive and after ubuntu install said installation failed due to hard drive error, I bought a new Super Talent 16GB solid state drive.
I think the 4GB is the bootable usb flash drive with ubuntu on it- I can't imagine what else it is.  There isn't any sd card in the card reader, and the only other storage drive on the computer is the 16GB SSD installed inside it.
Yeah, when I'm in partitioner trying to install, the 16GB is sda.
I can't get ubuntu to install in sda1, but it will in sda3.  Just, then it won't boot after it installs.

---

### Post by earlingy on 2010-07-15
After a long time away...this thread is resurrected! So...any ideas on how to get ubuntu to install?

---

