---
title: "Hard drive in Feisty recognised as hda"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2007-04-29
Reading others posts, Feisty uses the SATA driver for IDE hard drives resulting in sda designations. My hard drive (Maxtor 160G ATA100) is master on IDE0 and recognised as hda, why is this?

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda11
UUID=be675cfe-ba6d-4efe-a16f-42cea19013d7 /               reiserfs notail          0       1
# /dev/sda12
UUID=a1bc4b4c-a52a-4a57-b5b4-662208744d6b /home           reiserfs defaults        0       2
# /dev/sda1
UUID=44F450C5F450BB3E /media/sda1     ntfs    noauto,defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=1d92a1ae-f3b3-4c7c-b03c-8b21fd7667ff none            swap    sw              0       0


fstab uses sda designations but the kernel messages show as hda partitions

extract from dmesg:
[    7.774932] ReiserFS: hda11: checking transaction log (hda11)
[    7.803703] ReiserFS: hda11: Using r5 hash to sort names
[   16.434313] hdb: No disk in drive
[   33.535603] ReiserFS: hda12: found reiserfs format "3.6" with standard journal
[   33.535619] ReiserFS: hda12: using ordered data mode
[   33.541107] ReiserFS: hda12: journal params: device hda12, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   33.541553] ReiserFS: hda12: checking transaction log (hda12)
[   33.547450] ReiserFS: hda12: Using r5 hash to sort names
[   60.184719] cdrom: hdd: mrw address space DMA selected
[   62.232349] EXT3 FS on hda23, internal journal

I can also use hdparm:
root@orac:/home/anc# hdparm -tT /dev/hda

/dev/hda:
 Timing cached reads:   1998 MB in  2.00 seconds = 999.16 MB/sec
 Timing buffered disk reads:   92 MB in  3.05 seconds =  30.19 MB/sec

using Feisty 7.04, kernel 2.6.20-15-generic. Thanks in advance.

---

### Post by eurgain on 2007-05-10
Not quite right...

Feisty uses SATA drivers for SATA interfaces, and PATA drivers for PATA (aka IDE) interfaces.  Basically, PATA is a replacement for the ancient and broken IDE subsystem within the kernel.

A drive using PATA looks like a SCSI drive; for a user, this is clear because its device node is /dev/sd* rather than /dev/hd*

PATA is still quite new, and at least as late as 2.6.18 was still "Experimental".  I can only think that you have hardware that the PATA subsystem cannot yet deal with reliably, so the installer has dropped back to the old IDE system.  Either that, or it is just something strange with the way that Reiser generates kernel logs.

Can you post the output of:

# lspci|grep -i ide

and 

# ls -l /dev/hda*

This will show something about the disc control hardware you have and the devices that are present, which may yield an answer.

I am also puzzled about the numbers - hda10, hda11.  How many partitions do you have?!?

A

---

### Post by mjgumbley on 2007-05-10
Thanks for clarifying this - throughout the alternate CD's installer, (i.e. the partitioning tool), my disk partitions were referred to /dev/sda7 and /dev/sda5, which was rather confusing, since they're IDE, and IDE partitions have been /dev/hd* since the Dawn of Time. At the end of the installer, I chose to install GRUB - but the help text examples referred to /dev/hda* - leading to some confusion. (I entered /dev/hda7, which doesn't exist, so I had to go back and re-enter /dev/sda7)

Of course, if I'm using the alternative installer, I'm probably assumed to have some degree of clue - not sure if the partition naming is used inconsistently - and might lead to confusion. If so, this should probably be addressed.

---

### Post by eurgain on 2007-05-10
I think that the only issue that needs to be addressed is the confusion.  Apart from that, all seems fine.  

All SATA, PATA and SCSI discs now appear under /dev/sd*  The only silliness, really, is the 's' in /dev/sda1 (etc.) which is there by historical accident, when 's' stood for "SCSI", and later could pretend to stand for "serial" as in the 'S' in SATA.  Just think of PATA discs like you used to with SCSI emulation for ATA CD-writers back in the days of kernel 2.4.*, and you should be no more unhappy now than you were then.

The change from the IDE subsystem to PATA is quite major, and AFAIK, Feisty is the first mainstream distro to do this.  Certainly, FC6 and SUSE 10.2 still use IDE.  However, all the others will follow, I'm sure.  I have to say, that Ubuntu is not too good at making release notes to alert users to this type of change.

A

---

### Post by MartinDawson on 2007-05-13
I have got a problem with this...

The "SCSI" identities appear to be assigned as Ubuntu finds them on the IDE controllers.

By example, I have the standard two IDE connectors on the motherboard and a second two channel controller in a PCI slot.

The system HDD is on the motherboard IDE1 master, and the optical drive is the slave on IDE1.

I have four different PATA drives (in mobile rack slots) on the PCI controller.

When I installed the system, I had the top one of these mobile rack units unplugged. It was the master on IDE1 of the controller card.

Ubuntu assigned the following "SCSI" identities to the drives:

Mobo IDE1 Master - sda
PCI IDE1 Master - (not plugged in, not detected)
PCI IDE1 Slave - sdb
PCI IDE2 Master - sdc
PCI IDE2 Slave - sdd

Fair enough (though I should have seen the problem coming). I configured fstab to mount these at the appropriate points and set up Samba to start sharing on my LAN.

Then I did the extra bit of work on the hard drive in the top rack and slid it into position. When I rebooted the system, the identity assignments now looked like:

Mobo IDE1 Master - sda
PCI IDE1 Master - sdb
PCI IDE1 Slave - sdc
PCI IDE2 Master - sdd
PCI IDE2 Slave - sde

My physical drives had been reassigned identities! Of course, the fstab still made sense but the wrong drives were mounted to each point. Suddenly everybodies Samba drives had the wrong data on them. Sure, this is just my home NAS - but, even here, the scope for disaster is considerable.

I don't want my physical drives changing their identity. I can unplug a mobile rack, or a drive can go off line for any number of reasons. Imagine what happens when the drive mounted for backups suddenly turns into a   different drive - rsynch is going to dispose of the original data in short order...

Any advice on getting back to using physical (immutable) drive identities?

Cheers,
Martin

---

### Post by hal8000 on 2007-05-13
> **eurgain said:**
> Not quite right...
Can you post the output of:

# lspci|grep -i ide

and 

# ls -l /dev/hda*

This will show something about the disc control hardware you have and the devices that are present, which may yield an answer.

I am also puzzled about the numbers - hda10, hda11.  How many partitions do you have?!?

A


Sorry for delay, I have a multiboot system with 8 linux distros, FreeBSD, Solaris and Win XP.
I have 23 partitions in total on one 160G HD.

root@orac:/home/anc# lspci | grep -i ide
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)

root@orac:/home/anc# ls -l /dev/hda*
brw-rw---- 1 root disk 3,  0 2007-05-13 21:53 /dev/hda
brw-rw---- 1 root disk 3,  1 2007-05-13 21:53 /dev/hda1
brw-rw---- 1 root disk 3, 10 2007-05-13 21:53 /dev/hda10
brw-rw---- 1 root disk 3, 11 2007-05-13 21:53 /dev/hda11
brw-rw---- 1 root disk 3, 12 2007-05-13 20:53 /dev/hda12
brw-rw---- 1 root disk 3, 13 2007-05-13 21:53 /dev/hda13
brw-rw---- 1 root disk 3, 14 2007-05-13 21:53 /dev/hda14
brw-rw---- 1 root disk 3, 15 2007-05-13 21:53 /dev/hda15
brw-rw---- 1 root disk 3, 16 2007-05-13 21:53 /dev/hda16
brw-rw---- 1 root disk 3, 17 2007-05-13 21:53 /dev/hda17
brw-rw---- 1 root disk 3, 18 2007-05-13 21:53 /dev/hda18
brw-rw---- 1 root disk 3, 19 2007-05-13 21:53 /dev/hda19
brw-rw---- 1 root disk 3,  2 2007-05-13 21:53 /dev/hda2
brw-rw---- 1 root disk 3, 20 2007-05-13 21:53 /dev/hda20
brw-rw---- 1 root disk 3, 21 2007-05-13 21:53 /dev/hda21
brw-rw---- 1 root disk 3, 22 2007-05-13 21:53 /dev/hda22
brw-rw---- 1 root disk 3, 23 2007-05-13 21:53 /dev/hda23
brw-rw---- 1 root disk 3, 24 2007-05-13 21:53 /dev/hda24
brw-rw---- 1 root disk 3, 25 2007-05-13 21:53 /dev/hda25
brw-rw---- 1 root disk 3, 26 2007-05-13 21:53 /dev/hda26
brw-rw---- 1 root disk 3, 27 2007-05-13 21:53 /dev/hda27
brw-rw---- 1 root disk 3, 28 2007-05-13 21:53 /dev/hda28
brw-rw---- 1 root disk 3, 29 2007-05-13 21:53 /dev/hda29
brw-rw---- 1 root disk 3,  3 2007-05-13 21:53 /dev/hda3
brw-rw---- 1 root disk 3, 30 2007-05-13 21:53 /dev/hda30
brw-rw---- 1 root disk 3,  4 2007-05-13 21:53 /dev/hda4
brw-rw---- 1 root disk 3,  5 2007-05-13 21:53 /dev/hda5
brw-rw---- 1 root disk 3,  6 2007-05-13 21:53 /dev/hda6
brw-rw---- 1 root disk 3,  7 2007-05-13 21:53 /dev/hda7
brw-rw---- 1 root disk 3,  8 2007-05-13 21:53 /dev/hda8
brw-rw---- 1 root disk 3,  9 2007-05-13 21:53 /dev/hda9

I'm not sure if you use FreeBSD or Solaris but on both systems, a single partition is again sub-divided into a "slice".  For example on FreeBSD,  my 3rd primary partition, is divided into 
three slices, a /, a /home and an /opt slice, these are represented as hda28,hda29,hda30, so this is why the partition list contains more entries than actual partitions.

The individual slices can be found from the kernel messages:

root@orac:/home/anc# dmesg | grep hda2
[    6.115516]  hda2: <solaris: [s0] hda24 [s1] hda25 [s2] hda26 [s7] hda27 >
[    6.129252]  hda3: <bsd: hda28 hda29 hda30 >

---

