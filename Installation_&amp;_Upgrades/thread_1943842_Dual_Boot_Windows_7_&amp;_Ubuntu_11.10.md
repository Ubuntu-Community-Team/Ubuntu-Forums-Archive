---
title: "Dual Boot Windows 7 &amp; Ubuntu 11.10"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by apt-get install help on 2012-03-20
Hi

I have been researching how to Dual boot windows 7 & Ubuntu, but I can only find old post based on ubuntu 9.10.

Can someone please post an up to date post on how to achieve a successful dual boot system, which includes creating HDD partitions are solving boot loader problems?

Thanks :)

---

### Post by oldfred on 2012-03-20
there are a lot of threads. 

First how many primary partitions are used. Windows 7 installs often use all 4 primary partitions and you have to decide what to delete. 

Second backup and make Windows repairCD from the Windows recovery screen. Also make your system recovery set of DVDs.

Use Windows partition tools to shrink Windows and reboot several times so it can run chkdsk or make other fixes because of the resize. But do not create any new partitions as Windows often converts to dynamic partitions which does not work with Linux and even some Windows tools.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Some links to installs with screenshots:
Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by darkod on 2012-03-20
Also, if by any chance you are using EFI boot, I believe simply installing ubuntu will not create the dual boot correctly. oldfred has more info on that too.

---

### Post by apt-get install help on 2012-03-20
> **darkod said:**
> Also, if by any chance you are using EFI boot, I believe simply installing ubuntu will not create the dual boot correctly. oldfred has more info on that too.

I have a new system with 2TB HDD & UEFI BIOS

---

### Post by oldfred on 2012-03-20
Is Windows installed in MBR or gpt partitioning. Is efi the very first partition or a hidden 100MB boot partition which in efi would probably be second.

Post this:

sudo parted /dev/sda unit s print

---

### Post by apt-get install help on 2012-03-24
> **oldfred said:**
> Is Windows installed in MBR or gpt partitioning. Is efi the very first partition or a hidden 100MB boot partition which in efi would probably be second.

Post this:

sudo parted /dev/sda unit s print

Not done anything with the system yet, I will see how it goes.

---

### Post by oldfred on 2012-03-24
There were (are still?) some bugs in grub2/Ubuntu installer that overwrote the efi partition. So if you have the efi partition be sure to back up the Windows boot files in it first.

If you install Ubuntu first with a drive over 1+GB (not sure how much over) it will automatically format to gpt. But you do not have to have gpt until drive is over about 2.2GB or 2GiB. GUID(gpt) is the newer partitioning system over the 30 year old MBR(msdos) system that has been the standard since hard drives were added to PCs in the 1980's.

---

### Post by todd1049 on 2012-03-24
I am looking to install ubuntu on my laptop in a dual-boot setup with Windows 7, which is already installed.  Oldfred's post above says that one should use the Windows partition tool to shrink the Windows disk partition, but not to set up the other partitions.  I had used the Windows partition tool on an older machine to set up the partitions (this was with Windows Vista and ubuntu 8.04), and it worked fine.  Has anyone come across any particular reasons not to use the Windows 7 partition software for this purpose?  Thanks for your help.

---

### Post by Mark Phelps on 2012-03-24
> **todd1049 said:**
> Has anyone come across any particular reasons not to use the Windows 7 partition software for this purpose?  Thanks for your help.

Only one that I've seen -- that it won't allow you to shrink it as much as you want.

But ... it limits the shrinkage to prevent damage to the filesystem.  So, forcing it to shrink farther using a Linux utility, is simply asking for problems.

---

### Post by todd1049 on 2012-03-24
Mark Phelps, your comments are right on.  The Windows partition utility will not let me shrink the main partition as much as I might like.  But I have tried various utilities to fix this to little avail, and I don't plan to use gparted to try to force the issue and risk messing things up.

---

### Post by apt-get install help on 2012-03-24
I am having problems with booting ubuntu from a live CD.

The CD boots to the stage where the CD is checking the system and all components listing the names and vendor IDs in hex, that run down the terminal window in white text, it gets to my mouse lists its name and vendor ID of that and keeps listing it and it will not move on to the next stage of booting into Ubuntu.

System Spec

Processor (CPU) 

Intel® CoreTMi7-2600 Quad Core (3.40GHz, 8MB Cache) 

Motherboard 

ASUS® P8Z68-V/GEN3: PCI-E 3.0 READY, SLI, EFI BIOS

Memory (RAM)

32GB SAMSUNG DUAL-DDR3 1333MHz (4 X 8GB)

Graphics Card

2GB NVIDIA GEFORCE GTX 560 Ti - 2 DVI,HDMI,VGA - 3D Vision Ready

Memory - 1st Hard Disk

2TB WD CAVIAR GREEN WD20EARS, SATA 3 Gb/s, 64MB

Sound Card

Creative Sound Blaster® X-FiTM Xtreme Audio

Is the EFI and ACPI (Advanced Configuration and Power Interface) the cause of the problem?

Thanks

---

### Post by oldfred on 2012-03-24
I do not think it is efi and ACPI. But you should have AHCI enabled, but may need Windows drivers first.

Some threads where users did get efi to work.
dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)
How to install Ubuntu 11.10 on a Lenovo (U)EFI system (tested on S205, B570)
[http://ubuntuforums.org/showthread.php?t=1867367](http://ubuntuforums.org/showthread.php?t=1867367)
efi works with Asus P8H67 with EFI bios Do not recompile note:
[http://ubuntuforums.org/showthread.php?t=1896052](http://ubuntuforums.org/showthread.php?t=1896052)
So, in short: create the partitions on a non-EFI system, mkdir 2 folders and install. If I only knew from the start that it was this simple.

---

