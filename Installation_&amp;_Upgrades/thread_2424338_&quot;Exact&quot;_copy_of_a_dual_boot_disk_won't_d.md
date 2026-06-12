---
title: "&quot;Exact&quot; copy of a dual boot disk won't dual-boot"
date: 2019-08-07
forum: Installation &amp; Upgrades
---

### Post by orthoducks on 2019-08-07
I have a system which boots Ubuntu and Windows 7. It was set up the normal way: Windows installed first, then Ubuntu.

I'm trying to make an exact copy of my hard disk as a backup. I'm using the standalone version of PartitionWizard Pro 10, booted from a CD.

The copying operation was uneventful. When I disconnected the original disk and tried to boot from the copy, it went straight to Windows. No boot menu.

I found a dual-boot tutorial that said this means the UEFI settings are wrong and I should change them through the setup menu. I've got two issues with that. First, it doesn't make sense. UEFI settings are saved on the motherboard, not the disk. Replacing the disk with a supposedly exact copy should not affect them in any way.

Second... taking it on faith that this is the problem... I don't know how to fix it. UEFI settings let me control device order and disk priority, but I apparently need to specify what *partition* to boot from a given hard disk. I don't understand how to set that, or what value to set.

One more odd thing, which may or may not be relevant: The first (hidden) partition, where the boot software lives, is about 227 MB on the original disk and 100 MB on the copy. It appears to hold the same files, though. Apparently PartitionWizard doesn't make an *exactly* exact copy of the disk. I don't know why, or whether it matters, or what to do about it if it does.

---

### Post by wildmanne39 on 2019-08-07
*Thread moved to **Installation & Upgrades a more appropriate sub-forum**.*

---

### Post by Skaperen on 2019-08-07
apparently it does not make a true sector-by- sector copy.  are the 2 hard drives EXACTLY the same size or is there a slight difference?

i assume you can run with 2 drives attached.  are they both internal?  or is one of your drives an external one?

i'd like to see the output of the command "inxi -F" while you run Ubuntu from the original drive.

---

### Post by Skaperen on 2019-08-07
if your computer can run 2 internal hard drives at the same time the i suggest to install Windows on one drive and Ubuntu on the other one and do backups to an external USB hard drive using an rsync based tool run on Ubuntu with read access to the Windows drive..  if i had a need to run Windows dual-boot, this is what i would do.

---

### Post by Skaperen on 2019-08-07
my ultimate recommendation is to get a cheap 2nd computer to run Windows on.

---

### Post by TheFu on 2019-08-07
Use dd to clone the whole disk or a dd-like tool.  **ddrescue** is what I'd use, since it doesn't die at the first problem reading any sector.

/dev/sda is the whole disk.
/dev/sda1 is the 1st partition.
/dev/sda2 is the 2nd partition.

You want the whole disk so you get the boot, partition layout and everything else, so work at the /dev/sda device level.

Once you properly clone a disk in this way, you cannot insert both of them into the same computer at the same time.  The disk and partition identifiers will be identical, which will cause problems for any software which uses those identifiers ... like the boot stuff, partition mounting stuff, etc.

This assumes the 2 HDDs are identical models, though some people do use different models provided the target is exactly the same size or a little larger.  If they aren't the same exact size, the 2nd GPT copy at the end of the disk will be in the wrong place. I suppose there are ways to fix that. Pretty much every bit-for-bit cloning software has this requirement, so it isn't specific to dd/ddrescue.

I don't use image-based clones for backups.  Did long ago, but that was before UEFI existed.

There are at least 10 other bit-for-bit copy tools, so don't feel like you need to use dd or ddrescue.  Those are just the really simple, tiny, tools.  There are menu driven tools, but I always found them too confusing.   dd is already installed on every Unix system out there.  
If you have an Ubuntu Live desktop on a flash drive (any flavor will work), installing ddrescue into the live environment, assuming there is network connectivity, is 30 seconds.  Use it like it was really installed.  It will be gone at reboot, but that isn't a big deal.  The fact that it will work hard to clone sda to sdZ and get as many of the bits as possible, even with sector errors usually makes up for the slight inconvenience.  To clone sda to sdZ:
```
sudo ddrescue /dev/sda   /dev/sdZ   /tmp/logfile
```
Be certain when you do this that you are not running using either sda or sdZ for the current OS.

---

### Post by oldfred on 2019-08-07
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by orthoducks on 2019-08-08
Several suggestions here, and a really long answer seems necessary. I may or may not finish this tonight.

Skaperen: Yes, the two drives are exactly the same size (nominally 250 GB). I haven't added up the byte counts but I don't think disks of the same nominal size *can* be slightly different -- not if they both conform to ATA/SATA standards. In any case there's no difference big enough to account for the difference between a 227 MB original partition and a 100 MB copy. And in *any* case I'd expect a well-behaved program to distribute any size difference over all of the partitions (free space permitting, which it does), not stuff it all into one.

> i assume you can run with 2 drives attached. are they both internal? or is one of your drives an external one?

This is what I call a tabletop computer, in other words, breadboarded. Electronically, both drives are internal. Physically, both are external because the computer has no "inside."

>i'd like to see the output of the command "inxi -F"

I'll get it, but I'll have to do it from Linux.

>...i suggest to install Windows. on one drive and Ubuntu on the other...

That's an interesting idea, but not really attractive to me. Apart from the inelegance of using two disks to do the job of one, I don't see how it would help. I'd still need a dual boot capability, I'd still need to copy the disk it was on, and I would expect whatever went wrong to keep going wrong.

>my ultimate recommendation is to get a cheap 2nd computer to run Windows on.

Non-starter. I use the dual-boot system for testing hardware, and often I have to test the same hardware under Ubuntu and Windows. To do that, I just reboot. No way I'd want a setup that required me to move each component from one computer to another to test it completely!

TheFu:

>Use dd to clone the whole disk...

I looked at dd when I was trying to choose a tool, but that was a long, long time ago. I don't remember why I ruled it out... I think because I wanted something that would run standalone, for the maximum portability. I may look at it again. At this point, whatever my objection was, it may seem less important in light of the pain I'm going through.

oldfred: I'm not familiar with PPA, but it sounds like something that involves making another boot disk. I don't have time tonight, but I'll keep it in mind for the future.

---

### Post by orthoducks on 2019-08-08
From the Ubuntu system -- here's the inxi output.

[FONT=lucida console]
jonathan@jonathan-132-CK-NF79:~$ inxi -F
System:    Host: jonathan-132-CK-NF79 Kernel: 4.10.0-42-generic x86_64 (64 bit)
           Desktop: Unity 7.4.0  Distro: Ubuntu 16.04 xenial
Machine:   Mobo: EVGA model: 132-CK-NF79 v: 2
           Bios: Phoenix v: 6.00 PG date: 06/25/2008
CPU:       Quad core Intel Core2 Extreme X9650 (-MCP-) cache: 6144 KB 
           clock speeds: max: 3166 MHz 1: 3166 MHz 2: 3166 MHz 3: 3166 MHz
           4: 3166 MHz
Graphics:  Card: NVIDIA G92 [GeForce 8800 GT]
           Display Server: X.Org 1.18.4 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1680x1050@59.93hz
           GLX Renderer: GeForce 8800 GT/PCIe/SSE2
           GLX Version: 3.3.0 NVIDIA 340.102
Audio:     Card NVIDIA MCP55 High Definition Audio driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.10.0-42-generic
Network:   Card-1: NVIDIA MCP55 Ethernet driver: forcedeth
           IF: enp0s17 state: up speed: 100 Mbps duplex: full
           mac: 00:04:4b:16:b6:3e
           Card-2: NVIDIA MCP55 Ethernet driver: forcedeth
           IF: enp0s18 state: down mac: 00:04:4b:16:b6:3f
Drives:    HDD Total Size: 800.2GB (1.9% used)
           ID-1: /dev/sda model: Maxtor_7Y250M0 size: 250.1GB
           ID-2: /dev/sdb model: WDC_WD3000BLFS size: 300.1GB
           ID-3: /dev/sdc model: ST3250820AS size: 250.1GB
Partition: ID-1: / size: 123G used: 6.4G (6%) fs: ext4 dev: /dev/sda8
           ID-2: swap-1 size: 8.58GB used: 0.00GB (0%) fs: swap dev: /dev/sda5
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 53.0C mobo: N/A gpu: 55C
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 208 Uptime: 1:21 Memory: 894.2/7980.6MB
           Client: Shell (bash) inxi: 2.2.35 

[/FONT]

---

### Post by yancek on 2019-08-08
If you do not have an Ubuntu DVD/USB but can still boot the original Ubuntu, you can go to the boot repair site given above by oldfred and follow the instructions using the 2nd option on the page.  The ppa method will allow you to download and run boot repair on the running Ubuntu and you should select the Create BootInfo Summary option and post the link you are given when it finishes so that members will have details on your system.  Best not to try to make any repairs.

Did you install windows 7 yourself?  A default install of windows 7 would not be UEFI but rather a Legacy/CSM install so is your system UEFI or not.  Your info from the last post shows the BIOS as 10 years old.

> [FONT=lucida console]Bios: Phoenix v: 6.00 PG date: 06/25/2008[/FONT]

---

### Post by oldfred on 2019-08-08
Preferred way to run Boot-Repair is from Ubuntu live installer. The ppa is the way to add software to Ubuntu. See link to Boot-Repair on details. Do not download ISO as it is (was?) very old version.

Core 2 systems and those before about 2012 when Windows 8 was released are BIOS, not UEFI. UEFI is a new improved replacement for BIOS.

If you do a dd copy, you cannot keep both drives connected on reboot. You have duplicate UUIDs which is not allowed. Some have partially booted into one drive and then in other drive on reboot depending on which drive BIOS sees first.
If the software you used to copy, created new partitions & then new UUIDs, it will not boot as grub2 boot loader uses UUIDs to know which partition to boot from.

---

### Post by sudodus on 2019-08-08
You can use [Clonezilla](https://clonezilla.org) to clone a drive in a safe and efficient way. It can also create a compressed image (which can be used to recover a working copy of the drive).

dd (and ddrescue) can create an exact clone of a drive by copying each byte exactly from the source drive to the same position on the target drive.

One advantage with Clonezilla is that there are checkpoints, where you can double-check that it will do what you want (and not destroy valuable data by overwriting the wrong drive).

Another advantage with Clonezilla is that it is smart enough to identify and copy only used blocks of the drive. So it skips free blocks which can save a lot of effort and time.

-o-

If the target drive has the same size or is bigger, this will work directly to create a bootable drive, if the drive has an MSDOS partition table (MBR). If the drive has GUID partition table (GPT), there will be a problem with the backup partition table at the tail end of the drive, and it must be repaired (for example with gdisk or [gpt-fix](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix)). This is fairly easy.

But if the target drive is smaller (one single byte smaller), there will be more problems.

You cannot expect that drives with nominally the same size have exactly the same size. You must check it.

Use the command

```

sudo parted /dev/sdx u B p

```

to tell the exact size (in bytes) and also the partition table (MSDOS or GPT). Replace x with the actual device letter (for example a, b or c).

---

### Post by orthoducks on 2019-08-08
New development.

I've been pursuing several approaches to the backup problem concurrently, one of which is Clonezilla. Tonight I was able to clone my disk successfully with Clonezilla. I had some problems which I need to solve, but I'm going to start a separate thread for that.

Obviously this changes the priority of my appeal for aid with the "clone" produced by Partition Wizard. I'll try to return to this thread and wind it up cleanly -- I'd still like to have an alternative in my toolkit -- but it may be a while before I can do that.

Meanwhile, thanks to everyone who has been trying to help.

BTW, I wrote to MiniTool tech support (I have a paid copy of P.W.) but they begged off, saying that P.W. is a Windows tool and they really have no idea whether it works with Linux or not. According to plenty of Linux users it does, but the fact that the publisher won't back it up for that type of use has to weigh against it. When I find time to expand my toolkit I may well look for an alternative other than P.W.

---

### Post by VMC on 2019-08-09
Since you used a Windows backup program, try Macrium (the free version), it works great with Linux and Windows. I clone my HD and restored to a SSD using Macrium without issue. It recognizes linux labels, so its easy to see and not get confused.

But Clonezilla is Linux of choice, but I'm impressed with Macrium.

---

