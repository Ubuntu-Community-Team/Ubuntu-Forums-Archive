---
title: "Installer doesn't show any partitions"
date: 2010-09-19
forum: Installation &amp; Upgrades
---

### Post by mickeoliver on 2010-09-19
Hello,

recently I bought a new pc (acer m3203 with windows 7 home premium 64-bit) and decided to install ubuntu on it, alongside windows.

I downloaded ubuntu 10.04 64-bit desktop edition, and burnt it onto a cd.

The LiveCd works just fine, and so does the ubuntu installer up to the point where it asks for keyboard layout. After that, the installer goes straight to the "Prepare partitions" section, skipping the "Prepare disk space" section. It only shows an empty table.


[[IMG]http://img267.imageshack.us/img267/6910/installr.png[/IMG]]("http://img267.imageshack.us/i/installr.png/")

I have spent two days googling and experimenting, but with no success. Somewhere I was told to create an ext4 partition, didn't help. In another place they told me to change some BIOS settings, didn't help either. Somewhere they even told me that dual booting ubuntu 10.04 with windows is impossible, unless I use wubi.

Please help! I am  already getting very frustrated with ubuntu.

Micke Ahola

---

### Post by a_posse_ad_esse on 2010-09-19
Hi.  I would recommend using Wubi because it makes the installation/boot selection process much easier (though it isn't impossible).  You can run wubi from the CD you burned and it may give you a different result.

If it still doesn't show up, please provide some hardware information and we can look into it further.

---

### Post by sgbridges on 2010-09-19
I have the same problem.  I am also using the 10.04 x64 install cd.

My hardware is this,

[http://pc.ncix.com/ncixpc/ncixpc.cfm?uuid=1DF1D0CB-C012-4C42-8CE90CF4DA9A2153-3005934](http://pc.ncix.com/ncixpc/ncixpc.cfm?uuid=1DF1D0CB-C012-4C42-8CE90CF4DA9A2153-3005934)

---

### Post by a_posse_ad_esse on 2010-09-19
@sgbridges: Have you tried using Wubi?

---

### Post by mickeoliver on 2010-09-19
I tried installing wubi, but I just get the "No root filesystem is defined" error when I tried rebooting.

---

### Post by sgbridges on 2010-09-19
> **a_posse_ad_esse said:**
> @sgbridges: Have you tried using Wubi?

I run WUBI, after it restarts to complete the installation process, I get an error screen with a bunch of errors like,

 "can't open /dev/sda, No medium found"

---

### Post by srs5694 on 2010-09-19
The "can't open /dev/sda" error sounds like Ubuntu may lack drivers for whatever hard disk controller your computer uses. I can't be positive of that, though. As a first test of this hypothesis, you could boot from an Ubuntu Live CD, open a text-mode command prompt, and type "ls /dev/sd*". If you see any output, then the system is detecting the disk -- or at least the Live CD is. You could also type "lspci" and post the results here for analysis; somebody might recognize something that would be diagnostic.

Assuming the disk hardware *is* being detected, I recommend launching a text-mode shell and posting the output of "sudo fdisk -lu", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. This will tell us what your partition table looks like. Certain types of errors can cause some Linux partitioning tools (but not fdisk) to incorrectly display blank partition tables. I have a [Web page devoted to this topic,](http://www.rodsbooks.com/missing-parts/index.html) if you care to read up on it. That said, I'm skeptical that this specific problem is at work here, since the usual cause is a mis-sized extended partition, and few new computers ship with extended partitions.

---

### Post by sgbridges on 2010-09-19
> **srs5694 said:**
> The "can't open /dev/sda" error sounds like Ubuntu may lack drivers for whatever hard disk controller your computer uses. I can't be positive of that, though. As a first test of this hypothesis, you could boot from an Ubuntu Live CD, open a text-mode command prompt, and type "ls /dev/sd*". If you see any output, then the system is detecting the disk -- or at least the Live CD is. You could also type "lspci" and post the results here for analysis; somebody might recognize something that would be diagnostic.

Assuming the disk hardware *is* being detected, I recommend launching a text-mode shell and posting the output of "sudo fdisk -lu", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. This will tell us what your partition table looks like. Certain types of errors can cause some Linux partitioning tools (but not fdisk) to incorrectly display blank partition tables. I have a [Web page devoted to this topic,](http://www.rodsbooks.com/missing-parts/index.html) if you care to read up on it. That said, I'm skeptical that this specific problem is at work here, since the usual cause is a mis-sized extended partition, and few new computers ship with extended partitions.


Here is the requested info,

```



ubuntu@ubuntu:~$ ls /dev/sd*
/dev/sda  /dev/sdb  /dev/sdc

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:14.3 PIC: Intel Corporation 5520/5500/X58 I/O Hub Throttle Registers (rev 13)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
01:00.0 IDE interface: Device 1b4b:91a3 (rev 11)
02:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
03:00.0 VGA compatible controller: ATI Technologies Inc Device 6898
03:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
07:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

ubuntu@ubuntu:~$ sudo fdisk -lu
ubuntu@ubuntu:~$ 



```

---

### Post by srs5694 on 2010-09-19
Your "ls /dev/sd*" output shows that three hard disks are being detected; however, the fact the "fdisk -lu" returned with no output suggests that there's something seriously wrong with accessing them. Your lspci output includes the following line that identifies the hard disk controller:

```

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller

```

A little Googling suggests that this controller should be supported. My best suggestion at this point is to fiddle with your BIOS settings related to the hard disk (AHCI mode, etc.); however, if you've got Windows installed, that could disrupt Windows' ability to boot. Perhaps somebody else will have run into a similar issue and will be able to offer better advice at this point.

---

### Post by mickeoliver on 2010-09-20
I installed Ubuntu 9.04 successfully and then managed to upgrade.

(It uses original GRUB, not GRUB2 or something like that)

It works! Thanks.

---

### Post by Shadius on 2010-09-21
> **mickeoliver said:**
> I installed Ubuntu 9.04 successfully and then managed to upgrade.

(It uses original GRUB, not GRUB2 or something like that)

It works! Thanks.
I have the same problem as Mickeoliver. I reboot and get a message that says "No root file system is defined. Please fix this in the partition table." What does this mean and how do I fix this? I'm trying to use Wubi to install Ubuntu 10.04.

---

### Post by sgbridges on 2010-10-10
> A little Googling suggests that this controller should be supported. My best suggestion at this point is to fiddle with your BIOS settings related to the hard disk (AHCI mode, etc.); however, if you've got Windows installed, that could disrupt Windows' ability to boot. Perhaps somebody else will have run into a similar issue and will be able to offer better advice at this point.

I tried the latest Ubuntu release today, and changed the hard drive mode in BIOS from AHCI to IDE, but the installer still does not recognize my hard drive.

---

### Post by dino99 on 2010-10-10
the way to follow:

drop partedmagic on cd on usb stick, and prepare your partitions with it: [http://partedmagic.com/](http://partedmagic.com/)

then use the "alternate" iso to install ubuntu, and choose manual installation to choose your partitions made with partedmagic

the bios might run better if set to ahci or compatible (depend on bios maker)

if you have a fakeraid, see this thread first:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by sgbridges on 2010-10-11
> **dino99 said:**
> the way to follow:

drop partedmagic on cd on usb stick, and prepare your partitions with it: [http://partedmagic.com/](http://partedmagic.com/)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I booted with the partedmagic live cd, and it doesn't detect my disk either.

---

### Post by VMC on 2010-10-11
> **sgbridges said:**
> I booted with the partedmagic live cd, and it doesn't detect my disk either.

Boot up Windows and go to Disk Management. See how Windows displays your hard drive. If you can boot Windows, then obviously have a hard drive - ssd, sata, etc.

---

### Post by sgbridges on 2010-10-11
> **VMC said:**
> Boot up Windows and go to Disk Management. See how Windows displays your hard drive. If you can boot Windows, then obviously have a hard drive - ssd, sata, etc.

Attached image shows disk management in windows.  It's a 1TB drive, with 2 partitions.

---

### Post by VMC on 2010-10-11
From a Terminal type parted then print. You should see a list(like mine)
Also if nothing shows up, from parted type print devices. Type 'q' to end parted.

Also type from Terminal palimpsest, to see if any hard drive shows up:
```
(parted) **print device **                                                    
Model: ATA Hitachi HDT72106 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  113GB  113GB   primary   ntfs            boot
 2      113GB   535GB  422GB   primary   ntfs
 3      535GB   640GB  105GB   extended
 5      535GB   537GB  2097MB  logical   linux-swap(v1)
 6      537GB   548GB  10.5GB  logical   ext4
 7      548GB   558GB  10.5GB  logical   ext4
 8      558GB   569GB  10.5GB  logical   ext4
 9      569GB   640GB  71.3GB  logical   ext4
===
(parted) **print devices**                                                    
/dev/sda (640GB)

```

---

### Post by sgbridges on 2010-10-11
Here is the parted output 

```

root@PartedMagic:~# parted
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
GNU Parted 2.3
Using /dev/sr0
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print device
Error: Invalid partition table - recursive partition on /dev/sr0.         
parted: invalid token: device
Ignore/Cancel? i                                                          
Model: HL-DT-ST DVDRAM GH24LS50 (scsi)
Disk /dev/sr0: 137MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

(parted) q                                                                


```

---

### Post by sgbridges on 2010-10-11
Rebooting and using kubuntu to get palimpsest output which is attached as a screenshot.

---

### Post by VMC on 2010-10-11
This has to be BIOS related somehow.

From Windows open a CMD prompt and enter disk partitioning, but don't write anything:

> diskpart
> list disk
> ? (?-this will give you all the commands available)
When though, type 'exit'

---

### Post by sgbridges on 2010-10-11
> **VMC said:**
> This has to be BIOS related somehow.

From Windows open a CMD prompt and enter disk partitioning, but don't write anything:

> diskpart
> list disk
> ? (?-this will give you all the commands available)
When though, type 'exit'


```

Microsoft DiskPart version 6.1.7600
Copyright (C) 1999-2008 Microsoft Corporation.
On computer: SEAN-PC

DISKPART> list disk

  Disk ###  Status         Size     Free     Dyn  Gpt
  --------  -------------  -------  -------  ---  ---
  Disk 0    Online          931 GB  1024 KB
  Disk 1    No Media           0 B      0 B
  Disk 2    No Media           0 B      0 B

DISKPART> select disk 0

Disk 0 is now the selected disk.

DISKPART> detail disk

WDC WD1002FAEX-00Z3A0 ATA Device
Disk ID: BE82F852
Type   : ATA
Status : Online
Path   : 1
Target : 0
LUN ID : 0
Location Path : PCIROOT(0)#PCI(0100)#PCI(0000)#ATA(C01T00L00)
Current Read-only State : No
Read-only  : No
Boot Disk  : Yes
Pagefile Disk  : Yes
Hibernation File Disk  : No
Crashdump Disk  : Yes
Clustered Disk  : No

  Volume ###  Ltr  Label        Fs     Type        Size     Status     Info
  ----------  ---  -----------  -----  ----------  -------  ---------  --------
  Volume 1         System Rese  NTFS   Partition    100 MB  Healthy    System
  Volume 2     C                NTFS   Partition    471 GB  Healthy    Boot
  Volume 3     G   New Volume   NTFS   Partition    459 GB  Healthy

DISKPART>




```

---

### Post by esplinter on 2010-10-14
I solved this problem by removing the dmraid package before installing.

before launching the installer just run "sudo apt-get remove dmraid" and the lauch the installer and it should see your hard disk. 

hope it help.

---

### Post by alex88 on 2010-11-25
If you have non-raid hard disks. But i've setup 2 hdd in raid0 and removing dmraid or either trying to select ide,raid,ahci at bios don't change nothing. I'm still not able to find the hdd.

---

### Post by richard_wu0313 on 2010-11-25
win7 and ubuntu could be installed in the same machine. did you prepare a empty disk? ubuntu should be installed in a separate and empty disk. however, i do not suggest you to install two operation system, you can use vmware station/server to install virtual machine

---

### Post by alex88 on 2010-11-25
> **richard_wu0313 said:**
> win7 and ubuntu could be installed in the same machine. did you prepare a empty disk? ubuntu should be installed in a separate and empty disk. however, i do not suggest you to install two operation system, you can use vmware station/server to install virtual machine

That's not the problem, empty or not ubuntu can't see the raid disk, either it's empty.

---

### Post by thejhi on 2011-01-05
I exactly experimented the same issue.
Ubuntu installer was unable to show me the HDD till I typed in a terminal before installation "sudo apt-get remove dmraid".
Then, partionning was possible but only if I wanted to erase windows seven installation.
I found no mean to go further without removing windows.

If anyone has got a new idea to do so, i'm ok to receive the post !

---

### Post by fooman on 2011-05-23
digging up an old thread here i know....but just wanted to say thinaks for the the fix provided by esplinter!  :)

i started up my natty "live" usb flash drive and attempted to install onto a WD 150gb raptor (acer aspire desktop with windows 7 on half of the drive...not sure of which motherboard),  but the installer saw no partitions like the others in this thread.  

so while in the "live" environment,  i fired up gparted which allowed me to create my partitions (swap, /, and /home).  i then tried the installer again and it still refused to see any partitions.

so i opened a terminal and ran: sudo apt-get remove dmraid

when that was finished,  i again tried the installer and this time it worked without any problems.

thanks

---

