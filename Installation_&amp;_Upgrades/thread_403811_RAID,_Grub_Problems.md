---
title: "RAID, Grub Problems"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by docmarine on 2007-04-07
I am trying to install Feisty on a P4 3.2 HT with a Promise FastTrack S150 TX2Plus RAID SATA controller. The 2 HDD are identical. It is configured for "striping" through the "FastBuild" utility.

Ideally, I would like to setup Feisty using hardware striping, and the partitions using reiserFs.

The installer does not seem to reconize the array. I've tried installing to one drive, using the default layout provided by the installer... I get Grub error 2 in stage 1.5

Thanks in advance for any assistance.

docmarine

---

### Post by elvis on 2007-04-07
1) The Promise Fasttrack S150 is not a true RAID card.  It is a glorified SATA controller with supplied proprietary drivers that do RAID calculations on behalf of the kernel (not only that, but they don't support the LINUX kernel - only the WINDOWS kernel).  True RAID cards include a hardware processor on board (many inclide 333MHz Intel XScale chips these days) and will appear to your kernel as simple SCSI devices once you configure logical drives in the card's BIOS.  Examples of such cards are the Adaptec 3085 SATA RAID cards which retail for over US$400.  Just a hint: if you've paid under $100 for a "RAID" card, it's not "real" RAID.

2) Your best option is to use the card you've bought merely as a SATA controller and use Linux MD devices to build your RAID set.  Performance is no worse than what you would get using the "RAID" functions of the card itself (remembering again that these will be done in software anyway by a proprietary driver, and speaking from personal experience Linux's MD RAID performs better and is more reliable than any proprietary software RAID system I've seen or used in the last 10 years, which are quite a few).

Note that your /boot partition CANNOT be on a RAID stripe.  Why?  Well the kernel needs to load in order for the MD module to be inserted and used, but it can't do that if the kernel is contained on a striped disk.  The only RAID option you may choose for /boot is RAID1 (mirrored).  The reason is that the /boot partition can function as a single drive for read-access, and once the kernel and modules are loaded, the second drive can be added into the mirror.

If you want striping, it's recommended to set up your /boot partition as either a standalone non-RAID partition, or as a RAID1 on /dev/md0.  From there you can have your root / partition and any others in any form you like (RAID0 striping, RAID5 striping + CRC, etc).  Once your kernel and modules/init ramdisk are loaded from /boot, the other striped partitions are available for access via the kernel and md modules.

I personally never load my system on a striped set.  I always load my entire OS from a RAID1 mirror (or multiple mirrors, if I want to separate /, /var, /usr, etc), and then mount in another file system as a stripe somewhere else (usually making use of LVM for future upgradability).  That way you can separate your OS and user data, and know that even in the event of a single drive failure, your core system and setup are safe.

Generally speaking if you are using a stripe for fast data access, it's usually to acess large user files, and not core OS files.  No point risking your entire OS in that case.

---

### Post by docmarine on 2007-04-08
Thanks for the advice. The card came with the machine when i bought it (about 3.5 years ago). 
So in essence you are saying "break" the array that's created by the controller, and use the partitioner to achieve the desired result?

I've had enough of Windows, especially Vista with what I've seen on clients computers. Considering 95% of the work that I do is web-based, Linux seems like a good option. 
Thanks again.

docmarine

---

### Post by elvis on 2007-04-09
> **docmarine said:**
> Thanks for the advice. The card came with the machine when i bought it (about 3.5 years ago). 
So in essence you are saying "break" the array that's created by the controller, and use the partitioner to achieve the desired result?
Yes, that's what you need to do.  Essentially you are using the "RAID" card as just a SATA controller, and then letting the Linux kernel and software MD/RAID tools do the rest. 

You'll definitely find reporting and management tools to be superior in that regard (/proc/mdstat tells you what's going on, and mdadm lets you hot remove/add drives).  Performance will be the same or better.

> **docmarine said:**
> I've had enough of Windows, especially Vista with what I've seen on clients computers. Considering 95% of the work that I do is web-based, Linux seems like a good option. 
Thanks again.

docmarine

You're a patient man.  I got fed up with Microsoft's poor excuse for an operating system 7 years ago.  Under Windows, remote access is painful, user security is an oxymoron, and the need to constantly rely on third party black-list applications to stay virus free is just plain scary.  I admin evenly mixed networks of Windows, Linux and MacOSX machines, and the helpdesk stats reflect directly which OS causes the most issues and costs the most money over time.  And I'll give you a hint: it ain't the UNIX clones doing the damage. :)

---

### Post by Rmantingh on 2007-05-30
Hello,

I'm went through similar problems with my Promise FastTrak S150 TX2+ (2x120Gb).
I'm not particularly interested in RAID or Striping, just need to run Ubuntu on my
system in any way possible and need some handholding regarding partitioning.
I've deleted the array and went through a 'guided' setup/partitioning of Ubuntu
using the latest available Live CD but my system won't boot now as it doesn't
seem to recognize any bootable devices.
Ubuntu Live CD recognizes the drives and sees them as 2 separate disks (/dev/sda
and /dev/sdb). After having the installation process do the (guided) partitioning the
partition table for the first device (/dev/sda) looks like this:

Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13991   112382676   83  Linux
/dev/sda2           13992       14589     4803435    5  Extended
/dev/sda5           13992       14589     4803403+  82  Linux swap / Solaris

I'm a newbie regarding Linux and was wondering what the exact steps were
in getting Ubuntu to run from a system with the above Promise SATA controller.

Could it be that there is something that needs to be set in the BIOS?

Any help appreciated.

System:
Dell Dimension 8300
Promise FastTrak S150 TX2Plus (2x120Gb disks)
Ubuntu 7.04 Desktop i386

---

