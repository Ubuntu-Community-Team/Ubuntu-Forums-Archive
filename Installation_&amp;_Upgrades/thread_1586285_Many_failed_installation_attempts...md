---
title: "Many failed installation attempts.."
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by xd20 on 2010-10-01
A friend of mine suggested I finally try out a linux OS, and so I decided on what is apparently the most user accessible version.. well apparently not.

I've attempted to install it many times using various methods, all of which failed in different ways.

First I tried Wubi on 10.04, and right at the beginning of the boot up I get a measely "*Unable* to find a medium containing a *live filesystem*" error.  So I thought I'd try booting the disk and I didn't get the error, yay.  However, the ubuntu loading screen would either freeze or keep going in an endless cycle.  I know my PC isn't that slow, and after leaving the loading screen on for about an hour, I decided to call it quits on this version.

Later I came back to it, thinking perhaps a different medium would install properly.  So I attempted to use the USB method on the official site.  Similar results occured.. 

Finally I decided to try a different version.  Someone notified me that 8.04 didn't have the live filesystem error.  So I attempted a go at this version, and it made it passed the loading screen and such, but then there was a progress bar loading screen to which it froze about 15% of the way.  Another failed attempt. 

Then after seeking help, I came to find out about the alternate version.  So I downloaded and burned 10.04 alternate.  Finally, I boot it up and it loads flawlessly through the installation.  Then I came to the partition bit of the install.. this is the furthest I've gotten on any of the installs.  I set aside about 20 gb of space prior to booting it, so there was 20 gb of free space and about 18 gb for Windows XP above it.  (I intend on dual-booting) There was an option to automatically utilize the free space, and it allocated two partitions, an ext4 and a swap.  So that was good and fine.  Then upon finishing the partition information, it tried to create a file system on the ext4 and failed to do so.  Then it took me back to the partitioner where I was originally.  So I tried ext3, ext2 and various other ones, all failing.  So it wasn't the type of filesystem but something else entirely not allowing.  I figured maybe it was just my HDD.  

I decided to try the same thing with my secondary HDD, and the same thing happened.  It failed to create a filesystem.

I don't want to waste anymore bandwidth attempting to try every version out there... so are there any possible solutions?  

I've placed my DxDiag into the attachments as a txt file.

General Specs
-----------------
System Model: S6020WM (Compaq Presario)
BIOS: Phoenix - AwardBIOS v6.00PG
Processor: Intel Celeron CPU 2.60GHz
Memory: 1272MB RAM
Graphics: Nvidia Geforce 8400 GS 512 MB
HDD1 Model: WDC WD400EB-00CPF0
HDD2 Model: WDC WD800BB-00JHA0
CD/DVD Drive Model: AOPEN DUW1608/ARR

---

### Post by mikewhatever on 2010-10-01
Can you post the computer specs.

---

### Post by xd20 on 2010-10-01
I did.. in the attachment..

I just modified the original post to specify the general specs.

---

### Post by xd20 on 2010-10-02
Can anyone help me out please?

---

### Post by xd20 on 2010-10-02
no one? sigh

---

### Post by xd20 on 2010-10-02
Any help would be appreciated......

---

### Post by holiday on 2010-10-02
I suspect you have, with all these attempted installs, made a bit of a mess. Go into Windows and run a disc check. If all is good, then I suggest a format of your intended Ubuntu partition and then try the community standard install - no weird touches, no spooky new things. Just the tried and known to be true.

---

### Post by xd20 on 2010-10-02
Run chkdsk on the partition drive I'm going to use ubuntu on?  

The thing is, I don't make the ubuntu partition until the CD partitioner appears.. Would running the chkdsk work if I ran it on the whole HDD?

---

### Post by xd20 on 2010-10-02
> **holiday said:**
> I suspect you have, with all these attempted installs, made a bit of a mess. Go into Windows and run a disc check. If all is good, then I suggest a format of your intended Ubuntu partition and then try the community standard install - no weird touches, no spooky new things. Just the tried and known to be true.

Ok I ran chkdsk /f on the partition and it said there were errors found, and it resolved them.. so i boot up and redo the chkdsk and it still says there are errors, and i need to chkdsk /f to resolve them.. so i did that and then i boot up and did chkdsk again and it said their were errors and i need to do chkdsk /f to resolve them.. so i did that and.. ongoing cycle.

---

### Post by xd20 on 2010-10-02
No matter how many times I do chkdsk /f it still says I have errors. 

Also, on my 2nd HDD it says its perfectly fine, but I also tried to install onto it and that was also unsuccessful.

---

### Post by slooksterpsv on 2010-10-02
Sounds like either windows is corrupt and needs to be reinstalled or the HDD is possibly going bad, I would get the ISO from Western Digital to test your HDD and make sure they're not going bad. 

If all checks out with the WD drive test, it's Windows, it's corrupt and you'd want to run a chkdsk /R and see if it can recover data from sectors that may be corrupt. (WARNING WILL TAKE A WHILE TO COMPLETE) - Other than that, I would flatten the box (format it with dban to wipe the drive completely) then reinstall windows and ubuntu.

---

### Post by xd20 on 2010-10-02
Windows seems to work perfectly fine.. I've had 0 issues with anything.  And I'm not using dban because it would probably wipe my secondary HDD as well, and I can't have that.

And I have no clue of this WD test you're talking about.

---

### Post by lisati on 2010-10-02
> **xd20 said:**
> And I have no clue of this WD test you're talking about.

Some drives from Western Digital come with software to run diagnostics. One of mine come with software in a folder on the disk itself rather than on CD

---

### Post by xd20 on 2010-10-02
I found this pertaining to my HDD model: [http://support.wdc.com/product/download.asp?groupid=501&sid=3&lang=en](http://support.wdc.com/product/download.asp?groupid=501&sid=3&lang=en)

Perhaps that's the diagnostic program you're talking about?

---

### Post by slooksterpsv on 2010-10-02
> **xd20 said:**
> Windows seems to work perfectly fine.. I've had 0 issues with anything.  And I'm not using dban because it would probably wipe my secondary HDD as well, and I can't have that.

And I have no clue of this WD test you're talking about.

Sorry WD = Western Digital - WDC = Western Digital Caviar (drive model you have) - They have a hard disk utility which you run and it makes sure your Hard Drive is going bad.

Here's the link to it:
[http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en](http://support.wdc.com/product/download.asp?groupid=502&sid=3&lang=en) - that's the windows version.

---

### Post by xd20 on 2010-10-02
Lol that's what I linked.

---

### Post by xd20 on 2010-10-02
I did the Quick SMART tests on both my drives in the WD Test program and they both passed.

Should I do the extended test?

---

### Post by xd20 on 2010-10-02
I've done the extended test.  It passed as well.

So I don't think my harddrive at fault here.

Any other suggestions?

---

### Post by slooksterpsv on 2010-10-02
> **xd20 said:**
> I've done the extended test.  It passed as well.

So I don't think my harddrive at fault here.

Any other suggestions?

Hmm... try to manually create the partitions that you need in gparted. All you need is a swap and a / partition.

---

### Post by xd20 on 2010-10-02
I can't run gparted on Windows XP

---

### Post by slooksterpsv on 2010-10-02
> **xd20 said:**
> I can't run gparted on Windows XP

Run the live cd, and open software center and install it, otherwise you can download just gparted - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) - and burn it to a CD or USB Key

---

### Post by xd20 on 2010-10-02
If you recall, I can't run the liveCD... thus this thread in the first place.

I'll have to try the usb method for gparted and boot it up.

---

### Post by xd20 on 2010-10-02
Question about [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

I'm doing the manual method for MS Windows and it says to browse on my flash drive to makeboot.dat and click it.  Now, do I do that while still ON windows?  Or is there a way to browse to it on startup?  I've become confused.

---

### Post by holiday on 2010-10-02
> **xd20 said:**
> Ok I ran chkdsk /f on the partition and it said there were errors found, and it resolved them.. so i boot up and redo the chkdsk and it still says there are errors, and i need to chkdsk /f to resolve them.. so i did that and then i boot up and did chkdsk again and it said their were errors and i need to do chkdsk /f to resolve them.. so i did that and.. ongoing cycle.

Something went wrong. Your symptoms suggest very strongly that your Windows partition is corrupted. 

There may be utilities that can repair it. Google is your friend. 

Your next best hope, I think, is that your Windows recovery partition is ok, and that you're all backed up.

Somebody leap in to correct me. I so hope I'm wrong.

---

### Post by Hakunka-Matata on 2010-10-02
HI, I'm not sure from your posts how you are trying to install Ubuntu.  [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) url gives a comprehensive rundown on how to install it.  If you want to simply try it first without actually installing it, (it will run slow because it will be reading from the CD drive often) then download the latest Ubuntu version 10.04.  And next you must burn a CD to create the Boot CD.  This is all happening while you are up and running on your WINXP system.  Once you have the Ubuntu Install CD burned, set your BIOS to boot from CD first, put the CD in and reboot.  If it works out, you'll finally get a screen that asks if you want to install Ubuntu, or 'try it without installing it'.  Excuse me if I'm being too basic, perhaps you know all this, it wasn't obvious to me from reading your posts.

---

### Post by xd20 on 2010-10-02
> **Hakunka-Matata said:**
> HI, I'm not sure from your posts how you are trying to install Ubuntu.  [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer) url gives a comprehensive rundown on how to install it.  If you want to simply try it first without actually installing it, (it will run slow because it will be reading from the CD drive often) then download the latest Ubuntu version 10.04.  And next you must burn a CD to create the Boot CD.  This is all happening while you are up and running on your WINXP system.  Once you have the Ubuntu Install CD burned, set your BIOS to boot from CD first, put the CD in and reboot.  If it works out, you'll finally get a screen that asks if you want to install Ubuntu, or 'try it without installing it'.  Excuse me if I'm being too basic, perhaps you know all this, it wasn't obvious to me from reading your posts.

Please only allow the experts to give the advice.  I'm sorry, but you obviously have no idea of my problem if you're suggesting basic installation methods.

---

### Post by xd20 on 2010-10-02
> **holiday said:**
> Something went wrong. Your symptoms suggest very strongly that your Windows partition is corrupted. 

There may be utilities that can repair it. Google is your friend. 

Your next best hope, I think, is that your Windows recovery partition is ok, and that you're all backed up.

Somebody leap in to correct me. I so hope I'm wrong.

I'm on XP.. no recovery partition here.  All my important files however are on my secondary harddrive.  The only thing on the main HDD is windows XP and a bunch of program files.

---

### Post by xd20 on 2010-10-02
> **slooksterpsv said:**
> Run the live cd, and open software center and install it, otherwise you can download just gparted - [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) - and burn it to a CD or USB Key

I just attempted to place gparted on a usb I had.  It successfully booted up, but then upon selecting "GParted Live (Default Settings)" it went through various things on the command line, scrolling constantly, then suggesting error-codes.  Same occurrence when I tried the other modes.

I would burn it to a CD but I only have DVDs and I dunno if a DVD will work with the gparted ISO file.

---

### Post by xd20 on 2010-10-02
Just attempted a DVD version of GParted since I googled that it works.

It failed the same way the usb did.  So that's out the window.

Also, take note that partitioning was never actually a problem.  Whenever I used the partitioner in the alternate ubuntu 10.04 CD it worked great, creating the swap and ext4.  The issue was after i hit finish the partition and write files to disc, that's when it failed to place the file system on the ext4 / partition.  Same thing occurred with each type of format I did, whether it be ext3, ext2, etc.

So I don't think the partitioning was ever the issue.  It just doesn't want to write the file system to the partition.  I really don't like being led down these narrow paths of constant failure, and would prefer a suggestion that actually worked or at least progressed the installation to the next stage.

---

### Post by slooksterpsv on 2010-10-02
Backup needed files, reformat, reinstall. =D Like holliday said above, your windows partition seems to be fubar'ed

---

### Post by xd20 on 2010-10-02
Then why doesn't the install work on my 2nd hard drive?  It's got nothing to do with windows.

---

### Post by xd20 on 2010-10-02
I tried VirtualBox with my ubuntu liveCD and it failed.  But the alternate CD seems to be installing.  It made it passed the partitioning and is installing base files as we speak.

Of course, running it through virtualbox isn't exactly what I wanted, but its a good way for me to test some features.  VirtualBox seems awfully slow though.

---

### Post by xd20 on 2010-10-02
Is there any way to transfer/convert a VirtualBox ubuntu installation onto its own partition, if I allocate freespace on the HDD, that way I can dual-boot it alongside windows XP?

---

### Post by xd20 on 2010-10-03
If I were to format my entire first HDD, would ubuntu install successfully?  I don't wanna format it only to have the same issues I've been having.  Then have no OS to go back to.

---

### Post by slooksterpsv on 2010-10-03
> **xd20 said:**
> If I were to format my entire first HDD, would ubuntu install successfully?  I don't wanna format it only to have the same issues I've been having.  Then have no OS to go back to.

I can't say for sure... do you have an XP Cd you could boot from and get into recovery mode and run fixmbr and fixboot? By the way, what format are the partitions? Fat32 or NTFS?

---

### Post by holiday on 2010-10-03
Most Windows machines come with a recovery partition. Google your model and find the recovery bootup hotkey. 

Some recent Ubuntu installs have been trashing the recovery partition. We are hoping that you have dodged that bullet.

---

### Post by xd20 on 2010-10-04
Well actually I decided to format the entire drive and try to install ubuntu.  It failed, stating the same errors I had before..

Except I wrote down the liveCD error this time:

My instructions were to boot from liveCD, press F12, select language,
press F6 and put noacip and nomodeset, then delete "quiet splash --"

I did all that and here is the info I received.  
I changed random numbers to x and random letters to capital X and a 
? means it could be either letters or numbers.

Info given:

stdin: error 0
[  xx.xxxxxx]  isofs_fill_super: root inode is not a directory. Corrupted Media?
        mount: mounting /dev/sr0 on /cdrom failed: Invalid Argument


The error happened over and over for quite a while.. 
Then this occured:

[  xx.xxxxxx]  Corrupted Low Memory at c000xxXX (x??? phys) = 3691e001


This occured very quickly, possibly a few hundred times. But "3691e001" stayed the same.
Then it went back to the original error, about "corrupted media?" again.


Then after this occured it went into BusyBox with the error:

(initramfs) Unable to find a medium containing a live filesystem


And that was all, I typed reboot and took out the disc.


Then when that failed, I decided I'd just install windows 7.. lol

I still want ubuntu though.

---

### Post by slooksterpsv on 2010-10-04
[http://ubuntuforums.org/showthread.php?t=1337410](http://ubuntuforums.org/showthread.php?t=1337410)

There's something I would have never guessed. Give us the full stats of your system including video card, chipset, etc.

---

### Post by xd20 on 2010-10-06
My specs?

I've given them like three times in this thread..  but here they are, more specific than ever:

```

**Summary**
        Operating System
            MS Windows XP Professional 32-bit SP3
        CPU
            Intel Celeron
            Northwood 0.13um Technology
        RAM
            1.3GB DDR @ 133MHz (2-3-3-6)
        Motherboard
            MICRO-STAR INTERNATIONAL CO., LTD Gamila/Giovani/Neon series (Socket 478)    48 °C
        Graphics
            COMPAQ 7500 @ 1152x864
            512MB GeForce 8400 GS (PNY)    51 °C
            ForceWare version    258.96
        Hard Drives
            39.1GB Western Digital WDC WD400EB-00CPF0 (IDE)
            78GB Western Digital WDC WD800BB-00JHA0 (IDE)    46 °C
        Optical Drives
            AOPEN DUW1608/ARR
        Audio
            Realtek AC'97 Audio
**Operating System**
    MS Windows XP Professional 32-bit SP3
    Installation Date: 05 October 2010, 18:26
    Serial Number: *hidden*
**CPU**
        Intel Celeron
            Cores    1
            Threads    1
            Name    Intel Celeron
            Code Name    Northwood
            Package    Socket 478 mPGA
            Technology    0.13um
            Specification    Intel(R) Celeron(R) CPU 2.60GHz
            Family    F
            Extended Family    F
            Model    2
            Extended Model    2
            Stepping    9
            Revision    D1
            Instructions    MMX, SSE, SSE2
            Bus Speed    100.0 MHz
            Rated Bus Speed    400.1 MHz
            Stock Core Speed    2600 MHz
            Stock Bus Speed    100 MHz
                Caches
                    L1 Data Cache Size    8 KBytes
                    L1 trace cache    12 Kuops
                    L2 Unified Cache Size    128 KBytes
                Core 0
                    Core Speed    2600.6 MHz
                    Multiplier    x 26.0
                    Bus Speed    100.0 MHz
                    Rated Bus Speed    400.1 MHz
                        Thread 1
                            APIC ID    0
**RAM**
        Memory slots
            Total memory slots    2
            Used memory slots    2
            Free memory slots    0
        Memory
            Type    DDR
            Size    1280 MBytes
            DRAM Frequency    133.4 MHz
            CAS# Latency (CL)    2 clocks
            RAS# to CAS# Delay (tRCD)    3 clocks
            RAS# Precharge (tRP)    3 clocks
            Cycle Time (tRAS)    6 clocks
        SPD
            Number Of SPD Modules    2
                Slot #1
                    Type    DDR
                    Size    1024 MBytes
                    Manufacturer    PNY Electronics
                    Max Bandwidth    PC3200 (200 MHz)
                    Week/year    08 / 48
                    SPD Ext.    EPP
                        JEDEC #3
                            Frequency    200.0 MHz
                            CAS# Latency    3.0
                            RAS# To CAS#    3
                            RAS# Precharge    3
                            tRAS    8
                            Voltage    2.500 V
                        JEDEC #2
                            Frequency    166.7 MHz
                            CAS# Latency    2.5
                            RAS# To CAS#    3
                            RAS# Precharge    3
                            tRAS    7
                            Voltage    2.500 V
                        JEDEC #1
                            Frequency    133.3 MHz
                            CAS# Latency    2.0
                            RAS# To CAS#    2
                            RAS# Precharge    2
                            tRAS    6
                            Voltage    2.500 V
                Slot #2
                    Type    DDR
                    Size    256 MBytes
                    Manufacturer    Hyundai Electronics
                    Max Bandwidth    PC2700 (166 MHz)
                    Part Number    HYMD232 646B8J-J  
                    Serial Number    1C1AC064
                    Week/year    103 / 45
                    SPD Ext.    EPP
                        JEDEC #2
                            Frequency    166.7 MHz
                            CAS# Latency    2.5
                            RAS# To CAS#    4
                            RAS# Precharge    4
                            tRAS    8
                            Voltage    2.500 V
                        JEDEC #1
                            Frequency    133.3 MHz
                            CAS# Latency    2.0
                            RAS# To CAS#    3
                            RAS# Precharge    3
                            tRAS    6
                            Voltage    2.500 V
**Motherboard**
    Manufacturer    MICRO-STAR INTERNATIONAL CO., LTD
    Model    Gamila/Giovani/Neon series
    Version    0n31411RE101GIOVA10
    Chipset Vendor    Intel
    Chipset Model    i845G
    Chipset Revision    B1
    Southbridge Vendor    Intel
    Southbridge Model    82801DB (ICH4)
    Southbridge Revision    02
    Temperature    48 °C
        BIOS
            Brand    &oenix Technologies, LTD
            Version    3.26
            Date    05/09/2005
**Graphics**
        Monitor
            Name    COMPAQ 7500 on NVIDIA GeForce 8400 GS
            Current Resolution    1152x864 pixels
            Work Resolution    1152x836 pixels
            State    enabled, primary, output devices support
            Monitor Width    1152
            Monitor Height    864
            Monitor BPP    32 bits per pixel
            Monitor Frequency    75 Hz
            Device    \\.\DISPLAY1\Monitor0
        GeForce 8400 GS
            GPU    G98
            Device ID    10DE-06E4
            Revision    A2
            Subvendor    PNY (196E)
            Technology    65 nm
            Die Size    86 nm?
            Release Date    2008
            DirectX Support    10.0
            DirectX Shader Model    4.0
            OpenGL Support    3.0
            Bus Interface    PCI Express x0
            Temperature    51 °C
            GPU Clock    567 MHz
            Memory Clock    333 MHz
            Driver    nv4_disp.dll
            Driver version    6.14.12.5896
            ForceWare version    258.96
            BIOS Version    62.98.20.00.51
            ROPs    4
            Shaders    16 unified
            Memory    512 MB
            Bus Width    64 Bit
            Pixel Fillrate    2.3 GPixels/s
            Texture Fillrate    4.5 GTexels/s
**Hard Drives**
        WDC WD400EB-00CPF0
            Manufacturer    Western Digital
            Form Factor    GB/2.5-inch
            Serial Number    WD-WMAATJ868053
            Interface    IDE
            Capacity    39.1GB
            Real size    40,020,664,320 bytes
                S.M.A.R.T
                    01 Read Error Rate    200 (200 worst) Data 0000000000
                    03 Spin-Up Time    097 (092) Data 00000009E5
                    04 Start/Stop Count    097 (097) Data 0000000C23
                    05 Reallocated Sectors Count    200 (200) Data 0000000000
                    07 Seek Error Rate    200 (200) Data 0000000000
                    09 Power-On Hours (POH)    063 (063) Data 0000006C59
                    0A Spin Retry Count    100 (100) Data 0000000000
                    0B Recalibration Retries    100 (100) Data 0000000000
                    0C Device Power Cycle Count    097 (097) Data 0000000C17
                    C4 Reallocation Event Count    200 (200) Data 0000000000
                    C5 Current Pending Sector Count    200 (200) Data 0000000000
                    C6 Uncorrectable Sector Count    200 (200) Data 0000000000
                    C7 UltraDMA CRC Error Count    200 (253) Data 0000016447
                    C8 Write Error Rate / Multi-Zone Error Rate    200 (200) Data 0000000000
                    Status    Good
                Partition 0
                    Partition ID    Disk #0, Partition #0
                    Disk Letter    C:
                    File System    NTFS
                    Volume Serial Number    509128B7
                    Size    37.3GB
                    Used Space    6.25GB (17%)
                    Free Space    31.0GB (83%)
        WDC WD800BB-00JHA0
            Manufacturer    Western Digital
            Form Factor    GB/2.5-inch
            Serial Number    WD-WCAM91163509
            Interface    IDE
            Capacity    78GB
            Real size    80,026,361,856 bytes
                S.M.A.R.T
                    01 Read Error Rate    200 (200 worst) Data 0000000000
                    03 Spin-Up Time    166 (164) Data 0000000A7B
                    04 Start/Stop Count    092 (092) Data 0000002127
                    05 Reallocated Sectors Count    200 (200) Data 0000000000
                    07 Seek Error Rate    200 (200) Data 0000000000
                    09 Power-On Hours (POH)    067 (067) Data 0000005FFB
                    0A Spin Retry Count    100 (100) Data 0000000000
                    0B Recalibration Retries    100 (100) Data 0000000000
                    0C Device Power Cycle Count    099 (099) Data 000000075C
                    C2 Temperature    097 (074) Data 000000002E
                    C4 Reallocation Event Count    200 (200) Data 0000000000
                    C5 Current Pending Sector Count    200 (200) Data 0000000000
                    C6 Uncorrectable Sector Count    200 (200) Data 0000000000
                    C7 UltraDMA CRC Error Count    200 (200) Data 0000000006
                    C8 Write Error Rate / Multi-Zone Error Rate    200 (200) Data 0000000000
                    Temperature    46 °C
                    Temperature Range    ok (less than 50 °C)
                    Status    Good
                Partition 0
                    Partition ID    Disk #1, Partition #0
                    Disk Letter    D:
                    File System    NTFS
                    Volume Serial Number    7C562496
                    Size    72GB
                    Used Space    49GB (68%)
                    Free Space    23.5GB (32%)
                Partition 1
                    Partition ID    Disk #1, Partition #1
                    Disk Letter    E:
                    File System    FAT32
                    Volume Serial Number    FC9C7776
                    Size    2.41GB
                    Used Space    1.86GB (78%)
                    Free Space    564MB (22%)
**Optical Drives**
        AOPEN DUW1608/ARR
            Media Type    CD-ROM
            Name    AOPEN DUW1608/ARR
            Availability    Running/Full Power
            Capabilities    Random Access, Supports Removable Media
            Config Manager Error Code    Device is working properly
            Config Manager User Config    FALSE
            Drive    F:
            Media Loaded    FALSE
            SCSI Bus    0
            SCSI Logical Unit    0
            SCSI Port    1
            SCSI Target Id    0
            Status    OK
**Audio**
        Sound Card
            Realtek AC'97 Audio
        Playback Device
            Realtek AC97 Audio
        Recording Device
            Realtek AC97 Audio
**Peripherals**
        Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
            Device Kind    Keyboard
            Device Name    Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
            Location    plugged into keyboard port
                Driver
                    Date    7-1-2001
                    Version    5.1.2600.5512
                    File    C:\WINXP\system32\DRIVERS\i8042prt.sys
                    File    C:\WINXP\system32\DRIVERS\kbdclass.sys
        PS/2 Compatible Mouse
            Device Kind    Mouse
            Device Name    PS/2 Compatible Mouse
            Location    plugged into PS/2 mouse port
                Driver
                    Date    7-1-2001
                    Version    5.1.2600.0
                    File    C:\WINXP\system32\DRIVERS\i8042prt.sys
                    File    C:\WINXP\system32\DRIVERS\mouclass.sys
**Network**
    You are connected to the internet
    Connected through    Linksys Wireless-G PCI Network Adapter with SpeedBooster - Packet Scheduler Miniport
    IP Address    192.168.1.11
    External IP Address    **.**.***.***
    Adapter Type    Ethernet
        WinInet Info
            LAN Connection
            Local system uses a local area network to connect to the Internet
            Local system has RAS to connect to the Internet
        Wi-Fi Info
            Using native Wi-Fi API version    1
            Available access points count    1
                Wi-Fi (NETGEAR)
                    SSID    NETGEAR
                    Name    No name
                    Signal Strength/Quality    32
                    State    The interface is connected to a network
                    Dot11 Type    Infrastructure BSS network
                    Network    Connectible
                    Network Flags    Currently Connected to this network
                    Cipher Algorithm to be used when joining this network    No Cipher algorithm is enabled/supported
                    Default Auth used to join this network for the first time    IEEE 802.11 **Open System authentication algorithm**
        WinHTTPInfo
            WinHTTPSessionProxyType    No proxy
            Session Proxy
            Session Proxy Bypass
            Connect Retries    5
            Connect Timeout    60000
            HTTP Version    HTTP 1.1
            Max Connects Per 1.0 Servers    INFINITE
            Max Connects Per Servers    INFINITE
            Max HTTP automatic redirects    10
            Max HTTP status continue    10
            Send Timeout    30000
            IEProxy Auto Detect    No
            IEProxy Auto Config
            IEProxy
            IEProxy Bypass
            Default Proxy Config Access Type    No proxy
            Default Config Proxy
            Default Config Proxy Bypass

```

---

### Post by slooksterpsv on 2010-10-06
Do you have an onboard graphics controller? If so, can we remove the Nvideo GS 8400 and try booting off of the cd and see if that helps? The link I posted above, the whole issue was a PCI graphics card, actually if you have any addin cards that we could remove temporarily to see if we can get Ubuntu into the Live CD Portion, that would be best. Then slowly add each card back and find the troublesome one.

From looking up your computer, it should have onboard graphics. Let's try to use that, let me know what happens ok? (Crosses Fingers)

---

### Post by xd20 on 2010-10-06
> **slooksterpsv said:**
> Do you have an onboard graphics controller? If so, can we remove the Nvideo GS 8400 and try booting off of the cd and see if that helps? The link I posted above, the whole issue was a PCI graphics card, actually if you have any addin cards that we could remove temporarily to see if we can get Ubuntu into the Live CD Portion, that would be best. Then slowly add each card back and find the troublesome one.

From looking up your computer, it should have onboard graphics. Let's try to use that, let me know what happens ok? (Crosses Fingers)

I won't be doing that.  It defeats the purpose.  If I wanna dual-boot XP and Ubuntu and have to get rid of PCI cards in order to do it, its kind of pointless.

I have a wireless internet adapter and a graphics card in my PCI slots.  And I don't want to remove the card just so I can use ubuntu.  Not unless I can install ubuntu, then reinsert the card and it works.  But I doubt this is the case..

Plus my on-board graphics controller only has about 64 mb of video memory.  Why not just hop on MSN and we can discuss this further, if you'd like.

---

### Post by xd20 on 2010-10-06
But if you can guarantee my PCI cards will work with ubuntu after I install it and reinsert them, then I'll consider it.

---

### Post by xd20 on 2010-10-07
The issue has been partially resolved.

I took your advice and removed the PCI graphics card.  Ubuntu Wubi booted up successfully without a hitch.  My only issue was that it didn't know I had a wireless internet adapter PCI card in, and I didn't have internet access on ubuntu.  Surely there's a fix for this though.

The only issue, once I place my graphics card back in its PCI slot, ubuntu fails to boot up once again.  So after it failed, I thought I'd remove the card, and attempt to install the drivers for linux from nvidia onto ubuntu.  I did so, and reinserted the card after shutting down and then booting back up.  Ubuntu fails to load still.

So while this is solved, another issue arises.  How do we get our PCI graphic cards to work with ubuntu?  And how do we get it to recognize our internet adapter PCI card when it doesn't?

---

### Post by slooksterpsv on 2010-10-07
> **xd20 said:**
> The issue has been partially resolved.

I took your advice and removed the PCI graphics card.  Ubuntu Wubi booted up successfully without a hitch.  My only issue was that it didn't know I had a wireless internet adapter PCI card in, and I didn't have internet access on ubuntu.  Surely there's a fix for this though.

The only issue, once I place my graphics card back in its PCI slot, ubuntu fails to boot up once again.  So after it failed, I thought I'd remove the card, and attempt to install the drivers for linux from nvidia onto ubuntu.  I did so, and reinserted the card after shutting down and then booting back up.  Ubuntu fails to load still.

So while this is solved, another issue arises.  How do we get our PCI graphic cards to work with ubuntu?  And how do we get it to recognize our internet adapter PCI card when it doesn't?

Put in the PCI Wireless card and see if you can get on, if not, I'd suggest trying to wire it into your modem, download the latest updates (especially the Kernel updates) and then try putting in the GFX card and loading again. Good thing this is in Wubi

---

### Post by xd20 on 2010-10-07
The card as been in, and it went undetected.  Windows XP found it fine though.
And there is no modem, as this is a public wifi connection.

So I'm just gonna give up on ubuntu until they can manage to release an operating system that actually works properly.

---

