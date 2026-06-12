---
title: "gparted recognizes partitions, but installation wizard doesn't -- can't install"
date: 2013-12-10
forum: Installation &amp; Upgrades
---

### Post by sz-everythingelse on 2013-12-10
I'm running a Dell Optiplex 745 with a x64 processor. I have Windows 7 x64 installed.  
I have tried making the partitions with both windows tools and gparte and still the problem persists.
I don't have secure boot available on my BIOS.
For some reason the installation wizard doesn't seem to even register that there is a drive as I'm not given any options for installation.
No "Install next to..." or anything. Just a blank "Installation type" screen that gives me no partition options and if I click on the "+", "-", or "Change..." options I get an error that reads:
Sorry, Ubuntu 13.10 has experienced and internal error.
If you notice further problems, try restarting the computer.

If I open the details it states that "ubiquity crashed with TypeError in partman_dialog(): argument of type 'NoneType' is not iterable"

I would really like to be able to be able to install Ubuntu so any help working past this glitch will be much appreciated.
Thanks for your help

---

### Post by oldfred on 2013-12-10
While you have created an extended partition with swap inside it, you have used all 4 partitions and have no Linux formatted partition. Is sda3 intended for the install? If so you need to either change it from NTFS to ext4 and then use Something else or manual install or delete sda3, so the auto install may work.
I prefer manual install as with automation you get whatever it does.

---

### Post by sz-everythingelse on 2013-12-10
Thanks for your quick response.  
I've already tried using gparted to format the partitions as ext4 and swap, but the partitions are not recognized by ubiquity for some reason.  The screen capture that I posted shows that ubiquity does not populate any partitions that can be selected for root or swap.  I can even mount the partitions, which typically would result in an error message stating that you have to unmount them before proceeding, but in this case no error message and still no population of partitions.

---

### Post by fantab on 2013-12-10
In your screenshot, the partition /dev/sda4, labelled as 'Linux' is formatted with NTFS 'filesystem'. If you intend to install Ubuntu there you need to reformat it as 'Ext4'filesystem.
Also the supposed 'SWAP' is not a linux partition: it is formatted as FAT32 and merely labelled as 'SWAP'. The 'swap' partition must be formatted as 'SWAP'.
So 'FORMAT' your partitions for Linux.

See the screenshot to understand what I mean:

[ATTACH=CONFIG]248501[/ATTACH]

---

### Post by oldfred on 2013-12-10
Gparted did not used to show my XP drive that needed chkdsk. Click on red icon on your Windows installs and see what it says. The NTFS not mounting may prevent installer from seeing drive correctly.
Or do you have Windows hibernated?

---

### Post by sz-everythingelse on 2013-12-11
@FanTab: I tried that already, but I'll include a screen capture for you so you can see the results. 
@oldfred: I shutdown windows, I have even tried command line "shutdown -t 0" hoping that would help, but to no avail.  I have force mounted the drives and tried installing to no avail. I ran chkdsk and still a no go.
[ATTACH=CONFIG]248510[/ATTACH]

---

### Post by fantab on 2013-12-11
Post the output of the following commands: [Open Terminal to run commands]

```
sudo parted -l
sudo fdisk -l
```

---

### Post by sz-everythingelse on 2013-12-11
Model: ATA Hitachi HDT72502 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   198GB  198GB   primary   ntfs
 3      198GB   245GB  47.2GB  primary   ext4
 4      245GB   250GB  5244MB  extended                  lba
 5      245GB   250GB  5243MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!



Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b637b63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   385996799   192894976    7  HPFS/NTFS/exFAT
/dev/sda3       385996800   478150655    46076928   83  Linux
/dev/sda4       478152704   488394751     5121024    f  W95 Ext'd (LBA)
/dev/sda5       478154752   488394751     5120000   82  Linux swap / Solaris

---

### Post by oldfred on 2013-12-11
Partitions look normal to me.

Do you still have red icon on NTFS partition? And if you click or right click what does it say is the issue. Often just generic run chkdsk and possibly other issues.

Was drive ever gpt, LVM, dynamic in Windows, RAID, or other special formats. Those can leave meta-data on drive.

Then what setting is drive in BIOS. Some have issues if still IDE, should be AHCI or at least LBA or large.
Some find BIOS has drive turned off or other somewhat hidden or strange settings that can cause issues.
One user had BIOS set to boot from floppy drive, but had no floppy drive.
Another had a DVD in drive and with Ubuntu it was trying to run fsck on the DVD??
Some find only certain USB ports work.

---

### Post by sz-everythingelse on 2013-12-11
The red icon on the NTFS partition, if I right click and go to information, says:
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package. 
The following list of software packages is required for ntfs
file system support: ntfsprogs /ntfs-3g

The drive was never a special format. I couldn't find any setting in the BIOS for AHCI, but the drive is SATA and says that SATA operation is "normal" (which means that it is in native mode) opposed to "legacy" (which means it is compatible with older operating systems). I am using a DVD to install the operating system...can't seem to find any of my USB drives.

---

### Post by oldfred on 2013-12-11
How old is system? 

Some old systems will not boot from USB ports, and some real old Intel chips do not have PAE which newer versions of Ubuntu require. But most were 32 bit chips. Pentium M chips may be an issue, if that is what you have.

---

### Post by sz-everythingelse on 2013-12-11
I don't know the exact age of the unit, but it is newer than my other machine which has Ubuntu on it no problem. The processor is a Intel dual core x64 and it boots just fine from my USB external HD that I have Ubuntu on.

---

### Post by oldfred on 2013-12-11
Both my systems are dual core. My laptop was purchased two weeks before Vista (intentionally). It has 1.5GB of RAM and works with full Ubuntu but I do not use Unity but fallback with 12.04 64 bit.
I desktop with 4GB of RAM is similar vintage but bits and pieces updated every couple of years. 
Both install and run well, but I have nVidia on desktop, so I have to use nomodeset on every boot of installer or first boot after install to get video to work until I install the nVidia proprietary drivers.

Does external have entire / (root) partition inside the first 100GB. There are a few older systems, mostly USB external that have BIOS or grub issues and will not boot from beyond 100GB on a drive. They normally install ok but then just will not boot.

---

### Post by sz-everythingelse on 2013-12-11
Yes my external does have the entire / (root) on the first 100GB and it boots just fine. I don't want to have to use my external for Ubuntu on a regular basis, it's mostly been for recovery of files from other peoples machines and such. I rarely have a problem with my external not booting.

---

### Post by oldfred on 2013-12-11
I am running out of ideas, especially since it does boot from an external drive.

But I think you have to get rid of the red icon in gparted on your NTFS partition. That says there is some issue with Windows. Sometimes you have to run chkdsk more than once or until there are no errors.

---

