---
title: "Problem with download mirrors?"
date: 2013-08-30
forum: Installation &amp; Upgrades
---

### Post by Cyracus on 2013-08-30
When I try to download the 13.04 ubuntu desktop iso, on 3 separate machines on 3 separate networks and it gets to 28 MB and the download dies. When I download the 12.04 version it seems to download fine, but I try to install to my hard drive and it doesn't install properly, I've altered almost every setting in my bios (although I had a previous install on a separate hard drive that works fine, except the hard drive is over heating) but it either tells me to insert a proper boot media or it gives me a black screen with a blinking bar toward the top left corner. I know the system works as any other OS I can load onto it functions beautifully including other linux OS's (currently using mint and hating it)

My install method is uefi-usb (same as I use for other linux versions) here's my hardware profile as well
Mobo: ASUSTeK model: P8Z68-V PRO GEN3 version: Rev 1.xx Bios: American Megatrends version: 3012 date: 01/20/2012
CPU:       Quad core Intel Core i5-2500K CPU (-MCP-) cache: 6144 KB flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) 
           Clock Speeds: 1: 1600.00 MHz 2: 1600.00 MHz 3: 1600.00 MHz 4: 1600.00 MHz
Graphics:  Card: Advanced Micro Devices [AMD] nee ATI Barts PRO [Radeon HD 6850] 
           X.Org: 1.13.3 driver: fglrx Resolution: 1920x1080@60.0hz, 1280x800@60.0hz 
           GLX Renderer: AMD Radeon HD 6800 Series GLX Version: 4.2.12217 - CPC 12.104
Audio:     Card-1: Intel 6 Series/C200 Series Chipset Family High Definition Audio Controller driver: snd_hda_intel
           Card-2: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series] driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture ver: k3.8.0-19-generic
Network:   Card: Intel 82579V Gigabit Network Connection driver: e1000e 
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: c8:60:00:24:ec:a2
Drives:    HDD Total Size: 1000.2GB (0.4% used) 1: id: /dev/sda model: ST1000DM003 size: 1000.2GB 
Partition: ID: / size: 909G used: 4.1G (1%) fs: ext4 ID: swap-1 size: 8.56GB used: 0.00GB (0%) fs: swap 
RAID:      No RAID devices detected - /proc/mdstat and md_mod kernel raid module present

---

### Post by VMC on 2013-08-30
Have you tried a different _**[mirror]("https://launchpad.net/ubuntu/+cdmirrors")**_? It is strange that it completely stops if your using the same mirror as 12.04.

edit: _**[here's one from that list]("http://mirror.metrocast.net/ubuntu-releases/13.04/")**_. See if it works.

---

### Post by Cyracus on 2013-08-30
Just tried them again and they both seemed to work, still getting my issue. After boot up it says "reboot and select proper boot device or insert boot media in selected boot device and press a key" in troubleshooting I disconnected everuthing but my hard drive, rechecked my bios while checking help.ubuntu guide. Why does it hate me so?  My hard drive is a seagate ST1000DM003, can't find any info that says it would be incompatible, but it's the only change to my system I can track...if it is the problem, where would I look for the solution, if there is one that is

---

### Post by Cyracus on 2013-08-30
Used the boot info script from your sig and got this. Gonna try scrubbing my drive again and reinstalling to see if it helps. figured installing over mint which was working might help but...
=> No boot loader is installed in the MBR of /dev/sda.
 => No known boot loader is installed in the MBR of /dev/sdb.
 => No boot loader is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        /efi/linuxmint/grubx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       iso9660
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy

sdb2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1440036. According to the info 
                       in the boot sector, sdb2 has 0 sectors.
    Mounting failed:   mount: /dev/sdb1 already mounted or sdb1 busy
mount: /dev/sdb2 already mounted or sdb2 busy

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:

---

### Post by Cyracus on 2013-08-30
after soaking my hard drive in the irradiated waters of japan to thoroughly wipe it and installing xubuntu things work. now just to get it all set up. definitely liking XFCE. thanks for your time VMC

---

### Post by VMC on 2013-08-30
Your welcome.
HAHA, yea those waters will scrub anything off. I love Japan by the way. Was there for 7 weeks a few years ago. Loved it!

---

