---
title: "myriad install difficulties"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by piran on 2008-09-04
Wryly expect it's all probably my own fault but I *am*
having myriad difficulties getting ubuntu installed...
and I fondly expected it to be a little easier;~/

Existing W2kPro-SP4 workstation should dual boot but
ubuntu seemingly has disappeared without trace. The 
workstation boots into w2k without offering ubuntu. 

Have gone through the ubuntu 8.04 ALTERNATE install - 
ISO downloaded OK - burnt at a subnormal speed (after 
lurking through a few apposite postings) - internal
'check CD option' also completes testing successfully.
Opted for the given 'Guided install' though was some 
what surprised it chose an external FireWire box for
use as the SWAP drive. Though the workstation is not 
a 'RAID' box there are a good many connected drives.

The installer appropriately discovered the M$ OS 
during its GRUB phase and was given permission to 
suitably amend the MBR. I should now state that 
Acronis TrueImage 11 has made prior use of the MBR 
for its own necessary purpose. Possibly it is this
that is causing the no-show of the installed ubuntu?

Would appreciate advice as to what I might now do;~)

----best wishes, Robert

---

### Post by dstew on 2008-09-04
We need to do a little detective work to figure out how your system is currently configured before attempting a repair. Do you have an Ubuntu Live CD that you can boot? We can use some software on the Live CD system to analyse the problem.

---

### Post by piran on 2008-09-04
The LiveCD ran 'sort of' OK a day or two ago.
I attempted to use its install functionality
but kept getting 'error 141' in Guided mode
and all sorts of stuff in manual modes. So 
that's why I'm now down to the ALTERNATE cd.
My belief is that the installer is incorrectly
doing the GRUB phase and possibly attributing
inappropriate 'spare' drives and/or capacity.
Am now back in W2k licking my wounds;~/
----best wishes, Robert

---

### Post by piran on 2008-09-04
How do I securely/privately get a GIF file to you?
Snapshot of the manage layer of w2k's view of the drives.
----best wishes, Robert

[postedit: sent the GIF to the email address of your cpu place]

---

### Post by dstew on 2008-09-04
I see the picture. There are five drives, and it looks like the partitions that do not have a Windows-recognizable file system might be the Linux partitions. However, you can see that we will not be able to use the Windows tools to analyze the disks, because Windows will not cooperate in any way witn non-Windows file systems.

I understand that you were having a hard time installing from the Live CD. I asked you about the Live CD not to install, but to use the Live CD system to analyze your system. The Linux tools will be able to detect and analyze both Windows and Linux file systems, while Windows can only detect  and analyze Windows file systems.

Here is what I recommend as a first step. Boot the Ubuntu Live CD. Start the Terminal application (Applications --> Accessories --> Terminal). On the terminal command line enter```
sudo fdisk -l
```The output will be all the disks and partitions on your system that Linux can detect. Post the output to the forum.

---

### Post by piran on 2008-09-04
(posts crossed... now preparing a Live CD boot session...
unfortunately I have external commitments within the hour)

The workstation is a production W2kPro-SP4 installation.

ASUS motherboard support both SATA and PATA drives.
Between the BIOS running order, M$'s take on the drive
running order and finally Linux's take on the same all
adds up to organised hell. From my POV the OS should
handle the drives and just leave me the task of filling
them up with content;~) It's a running PC and ubuntu
is welcome to whatever capacity and drives it wants as
long as it does so appropriately ie non-destructively.

Confusingly the SATA drives are not attributed as being
primary or secondary and are attributed 'after' PATA
drives. Then the BIOS switches the boot order, which
changes the way M$ sees the drive order. Finally Linux
confusingly sees the drives in a different way too.

I had pre-arranged a 'spare' partition on the drive
used by the M$ OS and even formatted it with EXT3.
But the installer's 'Guided' mode seems to have just
ignored it. I thought it would be the best drive as it
would predicate an optimum location for GRUB.

Believe a likely resolution would be best found by
killing the ubuntu installer and manually placing drives
myself. With this in mind what are its requirements?
A partition of what capacity, on any particular drive
or controller and with what sort of mount( / or /root)?
Also a SWAP drive with similar queries?

----best wishes, Robert

---

### Post by piran on 2008-09-04
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x096f7846

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21690   174224893+   7  HPFS/NTFS
/dev/sda2   *       35847       36483     5116702+   7  HPFS/NTFS
/dev/sda3           31710       35846    33230452+  83  Linux
/dev/sda4           21691       31709    80477617+   5  Extended
/dev/sda5           21691       31295    77152131   83  Linux
/dev/sda6           31296       31709     3325423+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc36af073

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       52383   420766416    7  HPFS/NTFS
/dev/sdb2           52384       60801    67617585    5  Extended
/dev/sdb5           52384       60801    67617553+  bc  Unknown

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c02ec94

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sdc2            3917       82251   629225887+   f  W95 Ext'd (LBA)
/dev/sdc3           82252      121601   316078875   83  Linux
/dev/sdc5            3917       69192   524329438+   7  HPFS/NTFS
/dev/sdc6           69193       82251   104896386    b  W95 FAT32

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00032780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sde: 250.9 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x032320ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdf: 250.9 GB, 250999209984 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x196f15e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       21763   174811266    b  W95 FAT32
/dev/sdf2           21764       30515    70300440    5  Extended
/dev/sdf5           21764       30153    67392643+  83  Linux
/dev/sdf6           30154       30515     2907733+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by piran on 2008-09-04
Am now logged on thread using the LiveCD.
Previous posting shows the requested output.
What you see there that isn't particularly M$ 
is probably the detritus of all the failed install
attempts. I had earlier pre-prepared a 300GB
EXT3 partition for use by ubuntu and another
approx 30GB SWAP partition elsewhere. The 
'Guided' installer hasn't appeared to be on 
the same wavelength... I think some manual
intervention might repair the failed auto
installation. I've no email running on this
LiveCD iteration though the server will of 
course hold any such until I regain full 
control of operations;|)
best wishes, Robert

---

### Post by piran on 2008-09-04
Need to normalise the workstation before my departure.
Will resume later tonight or else tomorrow morning.
----best wishes, Robert

---

### Post by dstew on 2008-09-04
I agree the guided installation is not a good idea when you have as many disks as you have. I never use it to install Ubuntu.

I always prepare a root partition and a swap partition using the Gnome Partition Editor *before* I run the installer. It just gives me a feeling of security during the installation. 30 Gb is enough for the root partition, and 1 Gb for swap. You only have to create the partitions, there is no need to format them.

After you create the partitions, use the manual installation method. When you get to the partitioning step, you just pick the previously prepared partition for the root mount point (designated '/') and format it ext3. Note the Linux name of the partition (you can check using fdisk like you did above, to avoid confusion. Linux detects and names disks and partitions differently from Windows, and might number them differently than your BIOS). Select the previously set aside swap partition, and designate it "Use as swap". You do not have to format the swap partition. It should install the system fine at this point.

If you want to use the grub boot loader, you can install it into the MBR of the first disk. However, with the mix of disks you have, grub might get confused (actually it is the grub installer that gets confused). It is better to install grub by hand after the Linux OS is in. I can help you do that. If you want to install grub by hand, click the Advanced tab at the grub-install step, and choose not to install the boot loader.

---

