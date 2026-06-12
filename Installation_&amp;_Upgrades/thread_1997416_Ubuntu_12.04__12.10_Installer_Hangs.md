---
title: "Ubuntu 12.04 / 12.10 Installer Hangs"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by bluntbill on 2012-06-05
I have a Acer Aspire 7740G laptop into which I was trying to install Ubuntu 64 bit.

I have downloaded and live booted both 12.04 and 12.10 daily build, and both of them live boot correctly. I downloaded both versions in DVD.

When I try to install, the installer check for available disk space, wireless connectivity and AC power, and when I click continue on that screen, the installer never leaves the screen, the mose pointer changes to a waiting cursor and it just  stays there forever.

The installer does not stop responding, as I am able to click on cancel and it asks me if I want to leaves, and exits normally if I say yes. But it just doesn't pass that specific screen.

Is there an alternative method I can use to install? Or is there any known issue that might be causing this?

Best regards.

---

### Post by oldfred on 2012-06-05
Welcome to the forums.

Sometimes liveCD may use different defaults. Often video issue but that usually shows with liveCD.
Did you verify CD was correct. Or check ISO when downloaded? I would not be attempting 12.10 unless you want to help fix bugs like where installer does not work. There is a separate sub-forum for 12.10 and solving its issues.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If Video issue  or other boot parameter.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by bluntbill on 2012-06-05
Hello.

I might have not explained myself correctly, so I will try to give some more information.

I downloaded DVD ISO for version 12.04. I burned it into a DVD, and booted that DVD using 'Test without Installing'. So the DVD works, as I was able to boot UBUNTU with no problem. Video also worked, so that does not seem as a video problem.

Since the installer hung / stopped responding after checking for wireless, disk space and AC power, I thought it might be a bug and be resolved in the 12.10 version, even though that version is not a stable release yet.

So I downloaded 12.10, burned the ISO, booted the Live DVD, and tried to install after booting from LiveDVD. Same issue happenned.

Any thoughts?

Thanks in advance.

---

### Post by oldfred on 2012-06-05
Are you plugged into a Ethernet connection as wireless often needs to download drivers and during the install, that may not work.

Sometimes BIOS settings can also cause issues. Are you in IDE mode, it should be LBA, large or AHCI for most systems.

---

### Post by bluntbill on 2012-06-07
Hello.

Regarding BIOS, It is set with AHCI mode.

I am trying to install in a Laptop which has a wireless connection. I have tried both with wireless connected and disconnected, and same thing happens, it just stays in that page forever wth a loading icon as the mouse cursor...

Any other ideas?

Thank you for your help.

---

### Post by oldfred on 2012-06-07
It can also be video drivers.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

And if you have one of those switchable videos 
nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by bluntbill on 2012-06-09
Hello.

It does not seem to be a video problem as the image shows up fine.

I found some other threads regarding issues with disk access.

Here is a part of my /var/log/syslog, when my installer is at the screen where it seems to hang:

Jun  9 16:22:08 ubuntu kernel: [14043.249521] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:08 ubuntu kernel: [14043.249528] ata1.00: irq_stat 0x40000008
Jun  9 16:22:08 ubuntu kernel: [14043.249534] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:08 ubuntu kernel: [14043.249544] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:08 ubuntu kernel: [14043.249547]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:08 ubuntu kernel: [14043.249551] ata1.00: status: { DRDY ERR }
Jun  9 16:22:08 ubuntu kernel: [14043.249555] ata1.00: error: { UNC }
Jun  9 16:22:08 ubuntu kernel: [14043.257192] ata1.00: configured for UDMA/133
Jun  9 16:22:08 ubuntu kernel: [14043.257209] ata1: EH complete
Jun  9 16:22:10 ubuntu kernel: [14045.810903] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:10 ubuntu kernel: [14045.810910] ata1.00: irq_stat 0x40000008
Jun  9 16:22:10 ubuntu kernel: [14045.810916] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:10 ubuntu kernel: [14045.810926] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:10 ubuntu kernel: [14045.810928]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:10 ubuntu kernel: [14045.810933] ata1.00: status: { DRDY ERR }
Jun  9 16:22:10 ubuntu kernel: [14045.810937] ata1.00: error: { UNC }
Jun  9 16:22:10 ubuntu kernel: [14045.818660] ata1.00: configured for UDMA/133
Jun  9 16:22:10 ubuntu kernel: [14045.818681] ata1: EH complete
Jun  9 16:22:13 ubuntu kernel: [14048.372272] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:13 ubuntu kernel: [14048.372280] ata1.00: irq_stat 0x40000008
Jun  9 16:22:13 ubuntu kernel: [14048.372288] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:13 ubuntu kernel: [14048.372297] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:13 ubuntu kernel: [14048.372299]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:13 ubuntu kernel: [14048.372303] ata1.00: status: { DRDY ERR }
Jun  9 16:22:13 ubuntu kernel: [14048.372305] ata1.00: error: { UNC }
Jun  9 16:22:13 ubuntu kernel: [14048.379992] ata1.00: configured for UDMA/133
Jun  9 16:22:13 ubuntu kernel: [14048.380008] ata1: EH complete
Jun  9 16:22:16 ubuntu kernel: [14050.933687] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:16 ubuntu kernel: [14050.933694] ata1.00: irq_stat 0x40000008
Jun  9 16:22:16 ubuntu kernel: [14050.933700] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:16 ubuntu kernel: [14050.933711] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:16 ubuntu kernel: [14050.933713]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:16 ubuntu kernel: [14050.933718] ata1.00: status: { DRDY ERR }
Jun  9 16:22:16 ubuntu kernel: [14050.933721] ata1.00: error: { UNC }
Jun  9 16:22:16 ubuntu kernel: [14050.940382] ata1.00: configured for UDMA/133
Jun  9 16:22:16 ubuntu kernel: [14050.940402] sd 0:0:0:0: [sda] Unhandled sense code
Jun  9 16:22:16 ubuntu kernel: [14050.940405] sd 0:0:0:0: [sda]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jun  9 16:22:16 ubuntu kernel: [14050.940411] sd 0:0:0:0: [sda]  Sense Key : Medium Error [current] [descriptor]
Jun  9 16:22:16 ubuntu kernel: [14050.940418] Descriptor sense data with sense descriptors (in hex):
Jun  9 16:22:16 ubuntu kernel: [14050.940421]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Jun  9 16:22:16 ubuntu kernel: [14050.940434]         09 41 ad e7 
Jun  9 16:22:16 ubuntu kernel: [14050.940439] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
Jun  9 16:22:16 ubuntu kernel: [14050.940447] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 09 41 ad e7 00 00 01 00
Jun  9 16:22:16 ubuntu kernel: [14050.940460] end_request: I/O error, dev sda, sector 155299303
Jun  9 16:22:16 ubuntu kernel: [14050.940466] Buffer I/O error on device sda3, logical block 130516455
Jun  9 16:22:16 ubuntu kernel: [14050.940492] ata1: EH complete
Jun  9 16:22:18 ubuntu kernel: [14053.495054] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:18 ubuntu kernel: [14053.495058] ata1.00: irq_stat 0x40000008
Jun  9 16:22:18 ubuntu kernel: [14053.495062] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:18 ubuntu kernel: [14053.495068] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:18 ubuntu kernel: [14053.495069]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:18 ubuntu kernel: [14053.495072] ata1.00: status: { DRDY ERR }
Jun  9 16:22:18 ubuntu kernel: [14053.495073] ata1.00: error: { UNC }
Jun  9 16:22:18 ubuntu kernel: [14053.501649] ata1.00: configured for UDMA/133
Jun  9 16:22:18 ubuntu kernel: [14053.501668] ata1: EH complete
Jun  9 16:22:21 ubuntu kernel: [14056.056507] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:21 ubuntu kernel: [14056.056511] ata1.00: irq_stat 0x40000008
Jun  9 16:22:21 ubuntu kernel: [14056.056514] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:21 ubuntu kernel: [14056.056520] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:21 ubuntu kernel: [14056.056521]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:21 ubuntu kernel: [14056.056523] ata1.00: status: { DRDY ERR }
Jun  9 16:22:21 ubuntu kernel: [14056.056525] ata1.00: error: { UNC }
Jun  9 16:22:21 ubuntu kernel: [14056.062843] ata1.00: configured for UDMA/133
Jun  9 16:22:21 ubuntu kernel: [14056.062859] ata1: EH complete
Jun  9 16:22:23 ubuntu kernel: [14058.617868] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Jun  9 16:22:23 ubuntu kernel: [14058.617875] ata1.00: irq_stat 0x40000008
Jun  9 16:22:23 ubuntu kernel: [14058.617880] ata1.00: failed command: READ FPDMA QUEUED
Jun  9 16:22:23 ubuntu kernel: [14058.617891] ata1.00: cmd 60/01:00:e7:ad:41/00:00:09:00:00/40 tag 0 ncq 512 in
Jun  9 16:22:23 ubuntu kernel: [14058.617893]          res 41/40:00:e7:ad:41/00:00:09:00:00/40 Emask 0x409 (media error) <F>
Jun  9 16:22:23 ubuntu kernel: [14058.617898] ata1.00: status: { DRDY ERR }
Jun  9 16:22:23 ubuntu kernel: [14058.617901] ata1.00: error: { UNC }
Jun  9 16:22:23 ubuntu kernel: [14058.624267] ata1.00: configured for UDMA/133
Jun  9 16:22:23 ubuntu kernel: [14058.624296] ata1: EH complete

Does this give you any hint?

Thank you for your help.

---

### Post by bluntbill on 2012-06-09
After leaving the computer on that screen for over three hours, the installer passed on to another screen where I can choose If I want to leave windows and ubuntu side by side, if I want to overwrite windows, or another type of installation.

I chose another type of installation (don't quite remember the exact text on that option) and now the setup is at the following screen, scanning disks, and is taking forever again...

I assume that if I leave it there it will eventually get to another stage, but this does not seem like a normal behaviour, although I am not sure of this means and how to fix it...

Any ideas?

---

### Post by oldfred on 2012-06-09
It is looping thru the same error message, but I cannot tell what device is causing the error. It could be hard drive, CD, or something else plugged in or even that BIOS thinks is there. One user had floppy configured in BIOS but no floppy and had somewhat similar issue. Another was booting hard drive but it was trying to run a fsck on the CD. Any extra devices plugged in?

From liveCD can you go to Disk Utility and does it report hard drive as ok?

---

### Post by bluntbill on 2012-06-10
Hello.

I tried both testing my memory and disk and found no error.

The only device I have connected is an USB mouse.

Is there any other log file I can check to try and figure out what is causing this issue?

Or any type of command I can run by terminal or anything that tests the laptop for memory / disk or other type of problems or incompatibilities?

Thanks again for your help.

---

### Post by oldfred on 2012-06-10
Is drive encrypted or locked by BIOS?

Similar bug
[https://bbs.archlinux.org/viewtopic.php?id=78509](https://bbs.archlinux.org/viewtopic.php?id=78509)

What does this show?

sudo hdparm -I /dev/sda

---

### Post by bluntbill on 2012-06-13
Hello.

I don't think the disk is encrypted or locked, I am not even sure how to check for that, but I will look it in the BIOS.

By the way, I don't know if this may be causing any issues, but this laptop has Windows 7 installed in it, and I am trying to overwrite that installation with ubuntu.

Here is the output of the command:

/dev/sda:

ATA device, with non-removable media
    Model Number:       WDC WD6400BEVT-22A0RT0                  
    Serial Number:      WD-WX71A20L5876
    Firmware Revision:  01.01A01
    Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
    Supported: 8 7 6 5 
    Likely used: 8
Configuration:
    Logical        max    current
    cylinders    16383    16383
    heads        16    16
    sectors/track    63    63
    --
    CHS current addressable sectors:   16514064
    LBA    user addressable sectors:  268435455
    LBA48  user addressable sectors: 1250263728
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      610480 MBytes
    device size with M = 1000*1000:      640135 MBytes (640 GB)
    cache/buffer size  = 8192 KBytes
    Nominal Media Rotation Rate: 5400
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
    Advanced power management level: 254
    Recommended acoustic management value: 128, current value: 254
    DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
         Cycle time: min=120ns recommended=120ns
    PIO: pio0 pio1 pio2 pio3 pio4 
         Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
    Enabled    Supported:
       *    SMART feature set
            Security Mode feature set
       *    Power Management feature set
       *    Write cache
       *    Look-ahead
       *    Host Protected Area feature set
       *    WRITE_BUFFER command
       *    READ_BUFFER command
       *    NOP cmd
       *    DOWNLOAD_MICROCODE
       *    Advanced Power Management feature set
            SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    WRITE_{DMA|MULTIPLE}_FUA_EXT
       *    64-bit World wide name
       *    IDLE_IMMEDIATE with UNLOAD
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    Idle-Unload when NCQ is active
       *    NCQ priority information
       *    DMA Setup Auto-Activate optimization
            Device-initiated interface power management
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Long Sector Access (AC1)
       *    SCT LBA Segment Access (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
            unknown 206[14] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    162min for SECURITY ERASE UNIT. 162min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee600015b32
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 600015b32
Checksum: correct

---

### Post by oldfred on 2012-06-13
I think this is the problem:
> 
frozen

That has locked drive.

Check BIOS settings on drive for something that changes the setting.

[http://ubuntuforums.org/showthread.php?t=1982585](http://ubuntuforums.org/showthread.php?t=1982585)
Turned on AHCI and replugged in drive.

---

### Post by bluntbill on 2012-06-14
Hello.

Regarding AHCI, that mode is turned on.

When you say disconnecting and reconnecting the drive, you mean physically opening the laptop and disconnecting and reconnecting the cables that connect the motherboard to the laptop?

---

### Post by oldfred on 2012-06-14
If it is a laptop, I would try some other things, but do not know exact way. 

Try full power down and remove battery. 
Try changing BIOS and then if ok change back. 
Not sure what else.

---

### Post by bluntbill on 2012-06-15
Hello.

I have been trying to find some tool inside ubuntu that could perform some tests on my hard disk to check if everything was ok, and I am starting to think that the problem might be the disk.

I am not at my laptop now, but I used a program called gnome-disk or something similar, that has a SMART test (I think that's the name) that performs a self test on the disk. It has three modes, I tried all of them and the test failed on the disk for every test mode, mentioning it failed during a block read or something like that. The program had a note saying that a test failure meant that probably the disk would die in the following 24 hours :)

That seems promising...

I am planning on getting another hard disk and replacing my laptop's disk with that one, and checking if the problem goes away, just to make sure if the hard disk is causing the problem.

By the way, I tried turning off the laptop, removing thte battery, and checking every BIOS configuration for anything that might be locking the disk, and found nothing.

Thank you for your help.

---

### Post by bluntbill on 2012-06-19
Hello.

Just to report back.

I bought a new hard disk for my laptop and everything seems to be ok now. Unfortunately the problem seemed to be a faulty hard rive.

Thank you for your help.

---

### Post by Korn on 2012-10-06
Just booted the Ubuntu 12.10 beta from my USB stick and "sudo hdparm -I /dev/sda" reported that my drive was frozen. I had the same problem that after the screen where the Internet connection and disk space is checked the installer just hangs.

Then I followed this advice:
[http://tinyapps.org/docs/wipe_drives_hdparm.html#n2](http://tinyapps.org/docs/wipe_drives_hdparm.html#n2)

"sudo pm-suspend"
This is it. After waking up my notebook again the drive is now unfrozen.

The installation now continues successfully.

---

### Post by Barbalras on 2012-11-12
Hi!

I believe I have a similar issue. My 12.04 and 12.10 installations both hang right after hitting "continue" in the username step of the installation. My drive appears as frozen in hdparm but suspending doesn't change it to "not frozen".

What can I do?? thanks

---

