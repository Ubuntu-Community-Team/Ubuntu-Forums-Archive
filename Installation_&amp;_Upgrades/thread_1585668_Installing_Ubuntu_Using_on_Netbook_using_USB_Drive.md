---
title: "Installing Ubuntu Using on Netbook using USB Drive!!"
date: 2010-09-30
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2010-09-30
Hello all,
  I am going to be installing Ubuntu 10.0.4 netbook edition using a USB Drive.  I've already created a startupdisk using the USB drive and want to avoid wiping out Windows XP off the hard drive.  I have installed Ubuntu on an external USB harddrive before so I m familiar with partitioning, etc, and specifying partitions manually, however, I have never installed Ubuntu side by side another operating system, in this case Windows XP Professional, so my question is as follows:

Once I get to the installation portion and click on the advanced tab, what am I specifying for the partition table.  On my external usb harddrive partition it was pretty much structured like this:

hda[0] /dev/sda1
hda[1] /dev/sdb

I just want to know what to specify in the Advanced tab so that I can choose which operating system to boot up with at startup and so that I don't mess GRUB over and wipe out my Windows XP install.  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by Herman on 2010-09-30
You will need to be paying attention during the installation to see if your computer's BIOS reports the USB disk or the internal hard disk as '/dev/sda'.
Normally, the BIOS will count the internal hard disk as '/dev/sda', but in a few computers the USB drive will be counted as the first drive for some reason.

You will want to install GRUB to the same drive you are installing Ubuntu in, and if I understood your post correctly, that will be your netbook's internal drive, which has Windows XP in it . I guess you must be planning to shrink your Windows XP partition to make room for partitions for Ubuntu.

GRUB will be installed, (or is best installed), in the MBR of your first internal disk if you install Ubuntu inside your computer.
If you are installing Ubuntu in a removable drive like a USB external flash memory or USB external hard disk drive, then GRUB should be installed to MBR in the removable drive instead.

GRUB can safely be installed to MBR in a disk that contains other operating systems because the other operating system does not (normally) start at the MBR, but at the boot sector of the operating system's partition, sector 63 for Windows XP and earlier, or sector 2048 for Vista and later.
You can see that for yourself by running 'sudo fdisk -lu' from a Live CD or any Ubuntu installation.

The space in between the MBR and the boot sector of the first partition is usually left empty, and GRUB uses that part of the hard disk to embed its core image. GRUB's core.img in my computer fills up 49 sectors, so it's still a comfortable gap from the end of GRUB to the boot sector of the first partition.
As long as the Windows boot sector, (first sector of the Windows partition), is intact, Windows should be bootable, and GRUB uses the boot sector for a doorbell to wake up the Windows NTLDR loader which then boots Windows.

I have only ever run into one problem installing Ubuntu in a netboot with Windows XP which belongs to a friend. I think it might have been due to a buggy BIOS in that particular make and model of netbook and I needed to make myself a Windows7 installation DVD in a separate USB drive to upgrade the Windows XP boot sector to a Windows7 one, for some weird reason. Anyway, it was easy to fix and it worked in the end. Hopefully yours won't do that, I think I just ran into a freak problem that time.

---

### Post by freesparks on 2010-10-01
Hello Herman,

  I can't thank you enough for the reply.  Basically, for whatever reason, it seems like I installed it correctly.  This is the output that I get when I run this command:

> sudo fdisk -luI get this:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    12273659     6136798+  12  Compaq diagnostics
/dev/sda2   *    12273660   162468972    75097656+   7  HPFS/NTFS
/dev/sda3       162469888   307976191    72753152   83  Linux
/dev/sda4       307978238   312580095     2300929    5  Extended
/dev/sda5       307978240   312580095     2300928   82  Linux swap / Solaris

For whatever reason, I could not specify /dev/sda3 in the advanced tab during the install(it was just greyed out), after I specified swap as Logical and Beginning, should I have specified it at the end?  Everything seems to be normal as far as booting and I get to choose whether or not I want to boot with Linux or with its recoveries or Windows XP and its recoveries as well.  My last question is how I go about specifying just Windows XP and Ubuntu as the second option for booting.  I also was wondering if I can represent this graphically, meaning boot with a screen with the XP logo and the Linux Penguin instead of just a black screen with 6 options for booting with Linux as the default OS for booting.??  This netbook is for my 8 yearold cousin and it would be  good exercise in showing him the power of Linux over Windows and python programming.  Any help and resource would be greatly appreciated.

Best Regards,

freesparks

---

### Post by Herman on 2010-10-02
> For whatever reason, I could not specify /dev/sda3 in the advanced tab during the install(it was just greyed out),/dev/sda3 would indicate the first sector of your Ubuntu partition, and it is much better to install GRUB to a MBR rather than to a partition boot sector. 

> after I specified swap as Logical and Beginning, should I have specified  it at the end?   No, I don't think that where you put /swap would make a measurable difference. 

> Everything seems to be normal as far as booting and I  get to choose whether or not I want to boot with Linux or with its  recoveries or Windows XP and its recoveries as well.  Good. :)

---

### Post by Herman on 2010-10-02
> My last question is how I go about specifying just Windows XP and Ubuntu as the second option for booting.I don't agree that this is a good idea, but here it is anyway,
```
sudo mv 30_os-prober 06_os-prober
```
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

---

### Post by Herman on 2010-10-02
>  I also was wondering if I can represent this graphically, meaning boot with a screen with the XP logo and the Linux Penguin instead of just a black screen with 6 options for booting with Linux as the default OS for booting.?? 
This netbook is for my 8 yearold cousin and it would be good exercise in showing him the power of Linux over Windows and python programming. :) I think that feature (gfxmenu), will be available in GRUB sometime soon. Please refer to the following linked website, [GRUB Graphical Menu Development Journal]("http://grub.gibibit.com/Journal").

I have a web page about how to install a background image for GRUB if that will make you happy while we're waiting for gfxmenu to be available, [GRUB Splashimages]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Splashimages.html"). 
Regards, Herman :)

---

