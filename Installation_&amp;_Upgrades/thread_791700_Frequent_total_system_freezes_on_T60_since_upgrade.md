---
title: "Frequent total system freezes on T60 since upgrade to Hardy"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by Poilar on 2008-05-12
Since I upgraded to Hardy, I've been experiencing frequent total system freezes. At this point only my mute and unmute buttons appears to work and I have to hard boot my computer in order to restart. There appears to be no errors reported in my syslog. 

Just so you know, I use a Thinkpad T60 that previously worked perfectly on Gutsy (never had freezes before).

These freezes tend to happen when I don't touch the computer for a while (e.g. when I'm watching a movie fullscreen or when I go away and the screensaver is on). However, they don't occur 100% of the time when I'm away (e.g. two nights ago my computer still was working when I woke, but this morning it was frozen). 

Ideas?

Update: Since I switched my screensaver from a blank screen to something active, I no longer get freezes overnight. However, my computer still does periodically freeze when watching a video fullscreen.

---

### Post by VMC on 2008-05-12
> **Poilar said:**
> Since I upgraded to Hardy, I've been experiencing frequent total system freezes. At this point only my mute and unmute buttons appears to work and I have to hard boot my computer in order to restart. There appears to be no errors reported in my syslog. 

Just so you know, I use a Thinkpad T60 that previously worked perfectly on Gutsy (never had freezes before).

These freezes tend to happen when I don't touch the computer for a while (e.g. when I'm watching a movie fullscreen or when I go away and the screensaver is on). However, they don't occur 100% of the time when I'm away (e.g. two nights ago my computer still was working when I woke, but this morning it was frozen). 

Ideas?

Any log files to share? I'm assuming at that point you have to do a power cycle and reboot. I don't know what's inside a Thinkpad T60. Maybe a little rundown on video, cpu, and things. How about 'fdisk' output...okay I see no syslog errors. Does 'dmegs' give up anything?

---

### Post by Poilar on 2008-05-12
I don't believe there are any errors in dmesg, though I'm a little less clear as to what exactly dmesg contains. This creates a new file each boot, right? So, I need to look at dmesg.0 to see what happened before it crashed? There's nothing unusual at the end of the file.

Below are some maybe relevant outputs:

**fdisk output is as follows**:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4830    38796943+   7  HPFS/NTFS
/dev/sda2            6481        7296     6554520   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/sda3            4831        6480    13253625    5  Extended
/dev/sda5            4831        6219    11157111   83  Linux
/dev/sda6            6220        6480     2096451   82  Linux swap / Solaris

Partition table entries are not in disk order

**Here's the output of lshw -short so you can see my hardware**:

H/W path               Device      Class       Description
==========================================================
                                   system      1951WC4
/0                                 bus         1951WC4
/0/0                               memory      144KiB BIOS
/0/6                               processor   Genuine Intel(R) CPU           T2
/0/6/a                             memory      64KiB L1 cache
/0/6/c                             memory      2MiB L2 cache
/0/6/0.1                           processor   Logical CPU
/0/6/0.2                           processor   Logical CPU
/0/b                               memory      64KiB L1 cache
/0/29                              memory      1GiB System Memory
/0/29/0                            memory      512MiB SODIMM Synchronous
/0/29/1                            memory      512MiB SODIMM Synchronous
/0/1                               processor   
/0/1/0.1                           processor   Logical CPU
/0/1/0.2                           processor   Logical CPU
/0/100                             bridge      Mobile 945GM/PM/GMS, 943/940GML a
/0/100/2                           display     Mobile 945GM/GMS, 943/940GML Expr
/0/100/2.1                         display     Mobile 945GM/GMS/GME, 943/940GML 
/0/100/1b                          multimedia  82801G (ICH7 Family) High Definit
/0/100/1c                          bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c/0            eth0        network     82573L Gigabit Ethernet Controlle
/0/100/1c.1                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c.1/0          wmaster0    network     PRO/Wireless 3945ABG Network Conn
/0/100/1c.2                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1c.3                        bridge      82801G (ICH7 Family) PCI Express 
/0/100/1d                          bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.1                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.2                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.3                        bus         82801G (ICH7 Family) USB UHCI Con
/0/100/1d.7                        bus         82801G (ICH7 Family) USB2 EHCI Co
/0/100/1e                          bridge      82801 Mobile PCI Bridge
/0/100/1e/0                        bridge      PCI1510 PC card Cardbus Controlle
/0/100/1f                          bridge      82801GBM (ICH7-M) LPC Interface B
/0/100/1f.1            scsi4       storage     82801G (ICH7 Family) IDE Controll
/0/100/1f.1/0.0.0      /dev/cdrom  disk        DVDRAM GSA-4083N
/0/100/1f.2            scsi0       storage     82801GBM/GHM (ICH7 Family) SATA A
/0/100/1f.2/0.0.0      /dev/sda    disk        60GB HTS541060G9SA00
/0/100/1f.2/0.0.0/1    /dev/sda1   volume      36GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2   volume      6400MiB Windows FAT volume
/0/100/1f.2/0.0.0/3    /dev/sda3   volume      12GiB Extended partition


/0/100/1f.2/0.0.0/3/5  /dev/sda5   volume      10GiB Linux filesystem partition
/0/100/1f.2/0.0.0/3/6  /dev/sda6   volume      2047MiB Linux swap / Solaris part
/0/100/1f.3                        bus         82801G (ICH7 Family) SMBus Contro


Thanks!

---

### Post by VMC on 2008-05-12
I read someone had freezes while on battery , another while using multi-bay. 
Your running on AC when this happens, correct?

---

### Post by Poilar on 2008-05-13
Yeah, running on AC when this happens.

---

