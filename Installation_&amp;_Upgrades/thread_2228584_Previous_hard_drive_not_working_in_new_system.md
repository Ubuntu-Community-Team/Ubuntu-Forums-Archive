---
title: "Previous hard drive not working in new system"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by Simeon_Andrews on 2014-06-08
Summary of problem: I built a new desktop system, and pulled the 1.0 TB hard drive from my old computer to use as a data storage drive (plan to use 120 GB SSD for OS and programs). I was running Ubuntu 13.?? on my old system, and had no problems with the drive. However, the new system cannot write to the 1.0 TB hard drive, and only barely reads from it.

Details:
Me: casual Ubuntu user, just enough command-line comfort to do a little perl programming. Used Ubuntu as an OS for the past 3-4 years on my home system, but mostly just used for word processing, internet browsing, etc.

Old system:
M4A88T-M LE Asus motherboard
Corsair 2x 2GB RAM
WD10EARS Western Digital 1.0 TB Hard drive
AMD Phenom X2 555 Black Edition Processor
DVD-RW drive
plus sundry peripherals (no dedicated graphics card).
Running Ubuntu 13.??

New System:
GA-F2A88X-D3H Gigabyte motherboard
AMD A6-6400K Richland 3.9 GHz processor
Kingston HyperX Blue 1 x 8 GB RAM (DDR3, 1600 MHz)
Corsair 120 GB SSD CT120M500SSD1
plus 1.0 TB Hard drive and DVD-RW drive from above.

Background: Old system had some problems with power supply or the motherboard or the processor (issues with sleeping/restarting/waking up/powering down); rather than try to figure out which, I decided to just build a new system.

What I did: Bought a new case, installed all new components except the 1.0 TB hard drive and the DVD-RW drive, which I scavenged out of the old system. Before taking the old system apart, I downloaded the Ubuntu 14.04 image and  wrote the image to a DVD-R drive. Placed the DVD-RW drive in SATA0, SSD in SATA1, and old hard drive in SATA2. Booted from DVD drive, and installed on SSD. Was given the option of upgrading the previous version of Ubuntu (presumably on the old HD), replacing it, or choosing a different partition. I selected the SSD, formatted it in ext4 format, and clicked go. This was slow -- took a while at certain parts, but eventually finished with no stated problems. Then I started noticing issues:
a) Despite a faster processor, more memory, and a SSD boot drive, the system took much longer to boot than my old system (like 2-5 min)
b) boot from old drive (which should work, b/c it still had Ubuntu installed) did not work. Just gives a blank screen. Also true if I unplugged my SSD and tried that way; just wouldn't boot.
c) Once Ubuntu booted from the SSD, the 1 TB drive would show up, but when I tried opening it, it would take several minutes before showing the directory.
d) tried a read/write test from Ubuntu on the 1 TB drive. I can't recall the read speed readings, but then program gave an error and said it was unable to write to the drive. This despite accurately typing in the password for that system.
e) "top" shows no processes hogging more than 1% of CPU.

So, totally confused as to where to go from here. The whole system is pretty slow in booting, though programs and internet are generally snappy once the computer is booted. I most urgently need to access data on that 1.0 TB drive, but short of restoring my old system, I don't know what tricks to try. I would guess driver except that it worked fine on the old Ubuntu system, and it seems unlikely support would have been dropped in going to version 14.04.

Any help is appreciated!

---

### Post by oldfred on 2014-06-08
Something obviously not correct. My part 6 year old and part 4 year old system with a two year old slow SSD boots in  20 sec after BIOS/grub which is very slow and is 15 sec on its own (mostly BIOS) for a total of 35 sec.

But you seem to have several issues.
Did you set ownership & permissions on 1TB drive to match your current install?

I would also review logs. First log I look at is the boot log or what you see scroll by on booting if you remove quiet splash in grub. 

You may have log file viewer and look at /var/log/dmesg
or use any editor:
       gksudo gedit /var/log/dmesg

It is long, do not need to post entire thing. But it has time stamps and you want the entries with long times, outright errors, or repeated trys and then another entry later with success or failure.

Also with SSD you need to change a few settings to reduce writes. Although some say the new SSD have comparable lives to hard drives, so special settings are not required.

      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)
Similar to what I do, except I do use ext4 but without journel since partition is small, I use a daily cron task for trim, 
and I have Firefox on hard drive so no issues with cache. Swap is also on hard drive, but never used.
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Since a new system, did you install in UEFI boot or BIOS boot mode?
If only a Linux system often better to use gpt partitioning.
      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by Simeon_Andrews on 2014-06-08
Wow, thanks for that very helpful post! I will try to get to everything in a bit.

As to permissions, etc.: any recommendations on how to do this? I did not do anything in particular about them, so I'm sure I've screwed something up there, but I don't know enough to know what [IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG][IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]

As to UEFI or BIOS: no idea. I did whatever the default was; I wasn't given a choice. I will investigate and get back to you.
For now, here are the bits that seemed to maybe be "interesting" from the boot log:

0.195266] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.209685] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.209807] ACPI: No dock devices found.
[    0.210305] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210323] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210445] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210457] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210591] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.210602] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.217329] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.217335] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]

[    0.227365] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xffffffff] (subtractive decode)
[    0.228017] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 5 7 10 11 14 15) *0
[    0.228087] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 5 7 10 11 14 15) *0
[    0.228158] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 5 7 10 11 14 15) *0
[    0.228229] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 5 7 10 11 14 15) *0
[    0.228286] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 5 7 10 11 14 15) *0
[    0.228332] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 5 7 10 11 14 15) *0
[    0.228377] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 5 7 10 11 14 15) *0
[    0.228423] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 5 7 10 11 14 15) *0
[    0.228655] ACPI: \_SB_.PCI0: notify handler is installed
[    0.228695] Found 1 acpi root devices
[    0.228811] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none

[    0.253081] NET: Registered protocol family 1
[    0.253099] pci 0000:00:01.0: Boot video device
[    0.526414] PCI: CLS 64 bytes, default 64
[    0.526479] Trying to unpack rootfs image as initramfs...
[    0.766791] Freeing initrd memory: 18648K (ffff880035b84000 - ffff880036dba000)
[    0.850131] AMD-Vi: Found IOMMU at 0000:00:00.2 cap 0x40

Here's the bit where it looks like it's interfacing with the hard drives:
[    1.722088] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.722110] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.722127] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.722483] ata2.00: supports DRM functions and may not be fully accessible
[    1.724256] ata3.00: ATA-8: WDC WD10EARS-00Y5B1, 80.00A80, max UDMA/133
[    1.724260] ata3.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.724610] ata1.00: ATAPI: ATAPI   iHAS424   B, GL15, max UDMA/100
[    1.725300] ata2.00: disabling queued TRIM support
[    1.725305] ata2.00: ATA-9: Crucial_CT120M500SSD1, MU03, max UDMA/133
[    1.725307] ata2.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.725515] ata1.00: configured for UDMA/100
[    1.726769] ata3.00: configured for UDMA/133
[    1.727581] scsi 0:0:0:0: CD-ROM            ATAPI    iHAS424   B      GL15 PQ: 0 ANSI: 5
[    1.728805] ata2.00: supports DRM functions and may not be fully accessible
[    1.731109] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.731113] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.731255] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.731331] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.731632] ata2.00: disabling queued TRIM support
[    1.734922] ata2.00: configured for UDMA/133
[    1.735068] scsi 1:0:0:0: Direct-Access     ATA      Crucial_CT120M50 MU03 PQ: 0 ANSI: 5
[    1.735227] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.735245] sd 1:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.735247] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    1.735325] scsi 2:0:0:0: Direct-Access     ATA      WDC WD10EARS-00Y 80.0 PQ: 0 ANSI: 5
[    1.735364] sd 1:0:0:0: [sda] Write Protect is off
[    1.735366] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.735389] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.735459] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    1.735519] sd 2:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.735572] sd 2:0:0:0: [sdb] Write Protect is off
[    1.735574] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.735600] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.735754]  sda: sda1
[    1.736036] sd 1:0:0:0: [sda] Attached SCSI disk
[    1.782086] usb 4-4: new low-speed USB device number 2 using ohci-pci
[    1.782289]  sdb: sdb1 sdb2 < sdb5 >
[    1.782627] sd 2:0:0:0: [sdb] Attached SCSI disk
[    1.858063] tsc: Refined TSC clocksource calibration: 3892.922 MHz

The file ends at 4.85, having initiallized speakers. So I guess just 5 sec to boot? Except the experience was much longer, presumably once it started reading from the hard drives.

One other update: my wife succeeded today -- because she is more patient than I -- in reading files off the 1 TB drive -- it just took several hours to get them copied to an external hard drive.

---

### Post by Simeon_Andrews on 2014-06-08
Ah, just found the whole dmeg file (don't know why it was truncated earlier). In any event, this was interesting:

[    6.073733] init: plymouth-upstart-bridge main process ended, respawning
[    6.245944] wlan0: authenticate with c8:d7:19:19:1e:6e
[    6.553766] wlan0: send auth to c8:d7:19:19:1e:6e (try 1/3)
[    6.575752] wlan0: authenticated
[    6.577333] wlan0: associate with c8:d7:19:19:1e:6e (try 1/3)
[    6.601222] wlan0: RX AssocResp from c8:d7:19:19:1e:6e (capab=0x411 status=0 aid=2)
[    6.608952] wlan0: associated
[    6.608986] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   57.938367] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   57.938372] ata3.00: failed command: SMART
[   57.938376] ata3.00: cmd b0/da:00:00:4f:c2/00:00:00:00:00/00 tag 0
[   57.938376]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[   57.938378] ata3.00: status: { DRDY }
[   57.938381] ata3: hard resetting link
[   58.430522] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   58.436243] ata3.00: configured for UDMA/133
[   58.450554] ata3: EH complete
[  689.463519] systemd-timedated[2564]: /etc/localtime should be a symbolic link to a timezone data file in /usr/share/zoneinfo/.
[ 1711.694826] audit_printk_skb: 153 callbacks suppressed

So it looks like there was some problem in connecting to SATA3? No idea what would cause this...

---

### Post by oldfred on 2014-06-08
[   57.938367] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6[COLOR=#ff0000] frozen[/COLOR]

Frozen is not good.

And these:
[   58.450554] ata3: EH complete
[  689.463519] systemd-timedated[2564]: /etc/localtime should be a  symbolic link to a timezone data file in /usr/share/zoneinfo/.
[ 1711.694826] audit_printk_skb: 153 callbacks suppressed

Something about timezones and not sure what last entry relates to? All I can suggest there is a Google search.

My /etc/localtime is a 3.5kB file not a link. But I an currently using 12.04, just checked 14.04 and it is 3.6kB file.

       Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump
See this for some discussion of frozen, but I do not know if your BIOS set something or not?
man hdparm

Found a bug report on audit_printk_skb, but supposedly fixed.
[https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/937723](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/937723)

That may be saying you need some boot parameters to get your system to boot correctly. Or BIOS has settings that interfere?


What setting do you have in BIOS for drives? With an SSD it must be AHCI for trim to work.

---

### Post by Simeon_Andrews on 2014-06-09
Well, things get odder and odder... I tried removing the 1 TB drive from the system and was told there was no boot drive... in spite of having the SSD with the OS on it. So I reinstalled Ubuntu 14.04 on that drive. This was a long process, but seemed to go fine. Then today the computer just plain crased (Kernel panic) and stopped working. Boot was considerably faster once the 1 TB drive was removed from the system.

On the off chance the problems with the 1 TB drive wer with the cables/power, I unhooked the SSD and used those cables for the 1 TB drive; still won't boot. In any event, it's seeming to me more to be a problem with the motherboard/BIOS than with the drives themselves, as there seems to be instability with both drives. With this current setup -- only the 1 TB drive hooked up -- I put the Ubuntu DVD in drive and am running from that at the moment.

This allowed me to run sudo hdparam -I /dev/sda, which spit out the following:
ATA device, with non-removable media
    Model Number:       WDC WD10EARS-00Y5B1                     
    Serial Number:      WD-WCAV5N440187
    Firmware Revision:  80.00A80
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
    LBA48  user addressable sectors: 1953525168
    Logical/Physical Sector size:           512 bytes
    device size with M = 1024*1024:      953869 MBytes
    device size with M = 1000*1000:     1000204 MBytes (1000 GB)
    cache/buffer size  = unknown
Capabilities:
    LBA, IORDY(can be disabled)
    Queue depth: 32
    Standby timer values: spec'd by Standard, with device specific minimum
    R/W multiple sector transfer: Max = 16    Current = 16
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
            Power-Up In Standby feature set
       *    SET_FEATURES required to spinup after power up
            SET_MAX security extension
            Automatic Acoustic Management feature set
       *    48-bit Address feature set
       *    Device Configuration Overlay feature set
       *    Mandatory FLUSH_CACHE
       *    FLUSH_CACHE_EXT
       *    SMART error logging
       *    SMART self-test
       *    General Purpose Logging feature set
       *    64-bit World wide name
       *    {READ,WRITE}_DMA_EXT_GPL commands
       *    Segmented DOWNLOAD_MICROCODE
       *    Gen1 signaling speed (1.5Gb/s)
       *    Gen2 signaling speed (3.0Gb/s)
       *    Native Command Queueing (NCQ)
       *    Host-initiated interface power management
       *    Phy event counters
       *    NCQ priority information
       *    DMA Setup Auto-Activate optimization
       *    Software settings preservation
       *    SMART Command Transport (SCT) feature set
       *    SCT Write Same (AC2)
       *    SCT Features Control (AC4)
       *    SCT Data Tables (AC5)
            unknown 206[12] (vendor specific)
            unknown 206[13] (vendor specific)
Security: 
    Master password revision code = 65534
        supported
    not    enabled
    not    locked
        frozen
    not    expired: security count
        supported: enhanced erase
    216min for SECURITY ERASE UNIT. 216min for ENHANCED SECURITY ERASE UNIT. 
Logical Unit WWN Device Identifier: 50014ee205784866
    NAA        : 5
    IEEE OUI    : 0014ee
    Unique ID    : 205784866
Checksum: correct


Thus, there seems to be no known error there, as best as I can tell.

The lshw returned this for the hard drive:
 *-disk
       description: ATA Disk
       product: WDC WD10EARS-00Y
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: 80.0
       serial: WD-WCAV5N440187
       size: 931GiB (1TB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 sectorsize=512 signature=000cc65c

Again, all seems to be fine.
Couldn't run udisks b/c I'm running from the DVD.
I continue to be confused as to whether I'm using BIOS or UEFI. The motherboard firmware seems to refer to it as BIOS, generally, but the motherboard info claims it has "UEFI dual BIOS" so I wonder if it's actually running UEFI, but calling it BIOS so people know what it is?

Oh, and I checked, and it is using AHCI for the hard drives.

---

### Post by Simeon_Andrews on 2014-06-09
Duplicate post - deleted

---

### Post by oldfred on 2014-06-09
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Currently UEFI includes another chip to provide BIOS mode or backwards compatibility. 

Your drive showed this:
not    locked
        frozen

So not sure what issue is. Does Smart Status in Disks show drive is ok. All I know is that passed or green is good and anything else is not. But it can run lots of tests.

All these new UEFI systems, users must be consistent about installs. Either all BIOS or all UEFI or else you can only boot from UEFI menu and may have to turn on or off UEFI or CSM mode to change boot mode.

And how you partition drive and how you boot installer makes a difference on how it installs.
UEFI and BIOS are not really compatible, so once you start to boot in one mode you cannot change. Or you can only boot other systems from grub menu if in same boot mode. 
And how you boot install media is how it installs.

Windows & Ubuntu only boot in BIOS mode from MBR(msdos) partitioned drives.
UEFI requires gpt partitioned drives or both Windows & Ubuntu need gpt.
Ubuntu will will boot in BIOS or UEFI from a gpt partitioned drive, so if drive will not have Windows in BIOS mode ever, then I suggest gpt for future even if installing in BIOS mode currently. And include an efi partition at beginning of the drive.

---

### Post by Simeon_Andrews on 2014-06-19
OK, I've been trying a lot of things over the last couple of days, and here's where I'm at. I have since decided for certain that the 1.0 TB drive somehow got corrupted. When it is removed from the system, bootup is fast and with no problems. I changed the default settings in BIOS back to Windows 8 optimized, and it now sees my old 1.0 TB drive as well as everything else. I tried imaging the system, but got an error b/c the drive I was copying it to didn't have enough free spacer (a 958 GB image onto a 1.0 TB hard drive that already had 300 GB on it). However, where as early in the process of trying to rescue this drive (see above), the drive seemed to be accessible -- we were able to get the filesystem to mount and get some files (slowly) off of it once -- and one sector was said to be bad (in the "Disks" utility), now all sectors was bad, and attempting to get an image shows that it is all zeros.

The one thing I did that seems to (maybe) be the source of the problem is that I "formatted" it -- i.e. I changed it from "extended" to ext4 format. However, I did a "quick format" -- and I would have thought I knew I had done a full format, 'cause that would take a while with a 1.0 TB drive. So... do any of you have experience of getting any data off a drive that has been "quick formatted", seems to be all zeros, and in which ddrescue found nothing to rescue (despite a full sweep)? Or am I just plain completely out of luck?

---

### Post by oldfred on 2014-06-19
Testdisk or photorec. Or if NTFS and not free GetDataBack.
Testdisk has a deeper search and may show files. 
Photorec I have used and it is slow as it took me 8 hours on a much smaller drive. It  finds anything that looks like a file including deleted, but since file table is gone it is just using extension and you have to manually rename every file. Some tools will auto rename photos & music as they have internal data for naming.

Hopefully testdisk will work.
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

      
 NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)
For NTFS but may charge to actually get your data, but can run to see if it works better.
[http://ubuntuforums.org/showthread.php?t=2193293](http://ubuntuforums.org/showthread.php?t=2193293)
[http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810](http://ubuntuforums.org/showthread.php?t=2221353&p=13010810#post13010810)
[http://www.getdata.com/](http://www.getdata.com/)
For NTFS - GetDataBack often recommended
Caution: getdataback is not the same and is a scam.


 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by Simeon_Andrews on 2014-06-20
Thanks, oldfred. I'll check out those programs and see what I can do. I'm pretty sure this drive has never been in NTFS format, so I doubt that will work, but testdisk sounds like a good option to try.

---

