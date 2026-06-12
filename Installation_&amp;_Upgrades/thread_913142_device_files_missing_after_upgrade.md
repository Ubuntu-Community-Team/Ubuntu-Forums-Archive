---
title: "device files missing after upgrade"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by barrem01 on 2008-09-07
I just upgraded to Hardy Heron via the upgrade manager.

I let the manager do it's thing largely unattended, "choosing" the default whenever I noticed a prompt on the screen.

Now one of my disks doesn't mount.

The drive is still there in bios, but it looks like some of the device files didn't make it through the upgrade.

mike@ubuntu:~$ ls -l /dev/h*
crw-rw---- 1 root root 10, 228 2008-09-07 13:01 /dev/hpet

mike@ubuntu:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda2  /dev/sda5  /dev/sda6  /dev/sdb  /dev/sdb1


mike@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=637c862b-7d8f-49d4-8449-0cdab4d87493 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=07df6350-a93d-4134-9a98-6a5de1afd1b1 /donkey/ ext3 defaults 0 2
#/dev/hdb1       /space/hdb1     ext3    defaults        0       2
##/dev/sda1       /space/hdb1     ext2    defaults        0       2
# /dev/sda1 -- converted during upgrade to edgy
UUID=0b727638-bd22-4731-b9cb-8438253df36d /space/hdb1 ext2 defaults 0 0
# /dev/hdc1 -- converted during upgrade to edgy
UUID=1376c16e-5178-4828-b4dc-5ae99054c8b4 /space/hdc1 ext3 defaults 0 2
# /dev/hda6 -- converted during upgrade to edgy
UUID=e9fe0e55-2f11-4e6d-9b1b-1327ecac1db4 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

It seems as though the conversion moved /dev/hda* to /dev/sda*, and /dev/hdb* to /dev/sdb*, but when it came to what had been my /dev/sda* drive, it dropped the ball (and perhaps created /dev/sda6?).

Any suggestions on how to get the right device files created?

 - Mike

---

### Post by barrem01 on 2008-09-09
In a Linux Magazine Article by Frisch I found reference to "MAKEDEV" during the adding of new disks to a system.  

I found that 
sudo MAKEDEV sdc
would create files in /dev/.static/dev/

mike@ubuntu:/dev/.static/dev$ ls -l sdc*
brw-rw---- 1 root disk 8, 32 2008-09-09 00:05 sdc
brw-rw---- 1 root disk 8, 33 2008-09-09 00:05 sdc1
brw-rw---- 1 root disk 8, 42 2008-09-09 00:05 sdc10
brw-rw---- 1 root disk 8, 43 2008-09-09 00:05 sdc11
brw-rw---- 1 root disk 8, 44 2008-09-09 00:05 sdc12
brw-rw---- 1 root disk 8, 45 2008-09-09 00:05 sdc13
brw-rw---- 1 root disk 8, 46 2008-09-09 00:05 sdc14
brw-rw---- 1 root disk 8, 47 2008-09-09 00:05 sdc15
brw-rw---- 1 root disk 8, 34 2008-09-09 00:05 sdc2
brw-rw---- 1 root disk 8, 35 2008-09-09 00:05 sdc3
brw-rw---- 1 root disk 8, 36 2008-09-09 00:05 sdc4
brw-rw---- 1 root disk 8, 37 2008-09-09 00:05 sdc5
brw-rw---- 1 root disk 8, 38 2008-09-09 00:05 sdc6
brw-rw---- 1 root disk 8, 39 2008-09-09 00:05 sdc7
brw-rw---- 1 root disk 8, 40 2008-09-09 00:05 sdc8
brw-rw---- 1 root disk 8, 41 2008-09-09 00:05 sdc9

I found that after 
sudo MAKEDEV sdb

/dev/.static/dev had device files for sdb similar to those under /dev,
and that I could unmount /dev/sdb1 and mount /dev/.static/dev/sdb1 on the same mount point and be able to list the directory.  This indicated to me that MAKEDEV was making workable block special device files.

I ran MAKEDEV sdd through sdh followed with a mount attempt on sd?1 after each.  They all failed with the same error:

...
mike@ubuntu:/dev/.static/dev$ sudo mount -t ext2 /dev/.static/dev/sdf1/space/hdc1
mount: /dev/.static/dev/sdf1 is not a valid block device
mike@ubuntu:/dev/.static/dev$ sudo mount -t ext2 /dev/.static/dev/sdg1 /space/hdc1
mount: /dev/.static/dev/sdg1 is not a valid block device
mike@ubuntu:/dev/.static/dev$ sudo mount -t ext2 /dev/.static/dev/sdh1 /space/hdc1
mount: /dev/.static/dev/sdh1 is not a valid block device


I'm beginning to wonder if my hard disk just happened to fail during an OS upgrade.  Any clues would be welcome.

 - Mike

---

### Post by cdtech on 2008-09-09
You would just need to type the command in a terminal:
sudo fdisk -l

This will show all the partitions. Then you could edit your fstab file to include the missing drive.

---

### Post by barrem01 on 2008-09-09
> **cdtech said:**
> You would just need to type the command in a terminal:
sudo fdisk -l

This will show all the partitions. Then you could edit your fstab file to include the missing drive.

Hi cdtech,
Thank you for your reply.

My problem isn't in finding a specific partition on a recognized drive, it's finding a particular drive:

mike@ubuntu:/$ sudo fdisk -l
[sudo] password for mike:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000c511

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            9548       14593    40531995    5  Extended
/dev/sda2   *           1        9547    76686246   83  Linux
/dev/sda5            9731       14593    39062047+  83  Linux
/dev/sda6            9548        9729     1461852   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

all the sda and sdb partitions are doing what they are supposed to do.  It's the third drive, that can't be found, and for which device files no longer exist.  This drive is the only sata drive in the box, and is formated as a single ext2 partition.  It show in the bios, but not in ubuntu.

Thanks again for your suggestion.

 - Mike

---

### Post by barrem01 on 2008-09-14
So I opened the case.

The drive that ubuntu can't find is in there.  It's spinning.

I added another sata drive, since I intended to copy the contents of the drive that can't be accessed to another drive as soon as I find my way out of this maze.

The new sata drive can't be found either.

My bios reports my drives as being
ide1 Master  (my boot drive, pata)
ide2 Master  (another pata drive)
ide2 Slave   (my cd/dvd drive)
ide3 Master  (the old sata drive that used to work before the upgrade)
ide4 Master  (the new sata drive that's never been formated)

I booted from a trinity rescue disk to see if it gave me any ideas and some messages scrolled by that I thought were interesting.  So I checked for similar messages in /var/log/messages and here is what I found:


[HTML]
Sep 14 21:40:28 ubuntu kernel: [   18.417044] SCSI subsystem initialized
Sep 14 21:40:28 ubuntu kernel: [   18.455554] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 16
Sep 14 21:40:28 ubuntu kernel: [   18.455601] ACPI: PCI interrupt for device 0000:00:0f.0 disabled
Sep 14 21:40:28 ubuntu kernel: [   18.469645] usbcore: registered new interface driver usbfs
Sep 14 21:40:28 ubuntu kernel: [   18.469664] usbcore: registered new interface driver hub
Sep 14 21:40:28 ubuntu kernel: [   18.477905] scsi0 : pata_via
Sep 14 21:40:28 ubuntu kernel: [   18.489196] usbcore: registered new device driver usb
Sep 14 21:40:28 ubuntu kernel: [   18.490034] USB Universal Host Controller Interface driver v3.0
Sep 14 21:40:28 ubuntu kernel: [   18.498948] scsi1 : pata_via
Sep 14 21:40:28 ubuntu kernel: [   18.499964] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Sep 14 21:40:28 ubuntu kernel: [   18.499966] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Sep 14 21:40:28 ubuntu kernel: [   18.527214] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
Sep 14 21:40:28 ubuntu kernel: [   18.661892] ata1.00: ATA-6: WDC WD1200JB-00GVA0, 08.02D08, max UDMA/100
Sep 14 21:40:28 ubuntu kernel: [   18.661896] ata1.00: 234441648 sectors, multi 16: LBA48 
Sep 14 21:40:28 ubuntu kernel: [   18.677744] ata1.00: configured for UDMA/100
Sep 14 21:40:28 ubuntu kernel: [   18.712757] Floppy drive(s): fd0 is 1.44M
Sep 14 21:40:28 ubuntu kernel: [   18.736052] FDC 0 is a post-1991 82077
Sep 14 21:40:28 ubuntu kernel: [   19.004397] ata2.00: ATA-7: SAMSUNG SP2514N, VF100-41, max UDMA/100
Sep 14 21:40:28 ubuntu kernel: [   19.004401] ata2.00: 488397168 sectors, multi 16: LBA48 
Sep 14 21:40:28 ubuntu kernel: [   19.004418] ata2.01: ATAPI: TSSTcorpCD/DVDW SH-S182D, SB00, max UDMA/33
Sep 14 21:40:28 ubuntu kernel: [   19.044233] ata2.00: configured for UDMA/100
Sep 14 21:40:28 ubuntu kernel: [   19.216174] ata2.01: configured for UDMA/33
Sep 14 21:40:28 ubuntu kernel: [   19.216277] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00G 08.0 PQ: 0 ANSI: 5
Sep 14 21:40:28 ubuntu kernel: [   19.216363] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG SP2514N  VF10 PQ: 0 ANSI: 5
Sep 14 21:40:28 ubuntu kernel: [   19.217155] scsi 1:0:1:0: CD-ROM            TSSTcorp CD/DVDW SH-S182D SB00 PQ: 0 ANSI: 5
Sep 14 21:40:28 ubuntu kernel: [   19.217295] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 16
Sep 14 21:40:28 ubuntu kernel: [   19.217338] ahci 0000:00:0f.0: controller can't do NCQ, turning off CAP_NCQ
Sep 14 21:40:28 ubuntu kernel: [   19.217340] ahci 0000:00:0f.0: controller can't do PMP, turning off CAP_PMP
Sep 14 21:40:28 ubuntu kernel: [   19.222532] Driver 'sd' needs updating - please use bus_type methods
Sep 14 21:40:28 ubuntu kernel: [   19.222619] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Sep 14 21:40:28 ubuntu kernel: [   19.222629] sd 0:0:0:0: [sda] Write Protect is off
Sep 14 21:40:28 ubuntu kernel: [   19.222643] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 21:40:28 ubuntu kernel: [   19.222678] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
Sep 14 21:40:28 ubuntu kernel: [   19.222684] sd 0:0:0:0: [sda] Write Protect is off
Sep 14 21:40:28 ubuntu kernel: [   19.222695] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 21:40:28 ubuntu kernel: [   19.222697]  sda: sda1 <<4>Driver 'sr' needs updating - please use bus_type methods
Sep 14 21:40:28 ubuntu kernel: [   19.247180]  sda5 sda6 > sda2
Sep 14 21:40:28 ubuntu kernel: [   19.247264] sd 0:0:0:0: [sda] Attached SCSI disk
Sep 14 21:40:28 ubuntu kernel: [   19.247319] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Sep 14 21:40:28 ubuntu kernel: [   19.247328] sd 1:0:0:0: [sdb] Write Protect is off
Sep 14 21:40:28 ubuntu kernel: [   19.247342] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 21:40:28 ubuntu kernel: [   19.247373] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
Sep 14 21:40:28 ubuntu kernel: [   19.247379] sd 1:0:0:0: [sdb] Write Protect is off
Sep 14 21:40:28 ubuntu kernel: [   19.247390] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep 14 21:40:28 ubuntu kernel: [   19.247393]  sdb: sdb1
Sep 14 21:40:28 ubuntu kernel: [   19.250696] sd 1:0:0:0: [sdb] Attached SCSI disk
Sep 14 21:40:28 ubuntu kernel: [   19.254619] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep 14 21:40:28 ubuntu kernel: [   19.254635] sd 1:0:0:0: Attached scsi generic sg1 type 0
Sep 14 21:40:28 ubuntu kernel: [   19.254649] sr 1:0:1:0: Attached scsi generic sg2 type 5
Sep 14 21:40:28 ubuntu kernel: [   19.266527] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Sep 14 21:40:28 ubuntu kernel: [   19.266533] Uniform CD-ROM driver Revision: 3.20
Sep 14 21:40:28 ubuntu kernel: [   20.218702] ahci 0000:00:0f.0: AHCI 0001.0000 32 slots 4 ports 3 Gbps 0xf impl IDE mode
Sep 14 21:40:28 ubuntu kernel: [   20.218707] ahci 0000:00:0f.0: flags: 64bit pm led clo pio slum part 
Sep 14 21:40:28 ubuntu kernel: [   20.219059] scsi2 : ahci
Sep 14 21:40:28 ubuntu kernel: [   20.219333] scsi3 : ahci
Sep 14 21:40:28 ubuntu kernel: [   20.219430] scsi4 : ahci
Sep 14 21:40:28 ubuntu kernel: [   20.219523] scsi5 : ahci
Sep 14 21:40:28 ubuntu kernel: [   20.219952] ata3: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd00 irq 221
Sep 14 21:40:28 ubuntu kernel: [   20.219955] ata4: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffd80 irq 221
Sep 14 21:40:28 ubuntu kernel: [   20.219958] ata5: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe00 irq 221
Sep 14 21:40:28 ubuntu kernel: [   20.219961] ata6: SATA max UDMA/133 abar m1024@0xfebffc00 port 0xfebffe80 irq 221
Sep 14 21:40:28 ubuntu kernel: [   20.694511] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [   50.664746] ata3.00: qc timeout (cmd 0xec)
Sep 14 21:40:28 ubuntu kernel: [   50.664752] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 14 21:40:28 ubuntu kernel: [   50.664754] ata3: failed to recover some devices, retrying in 5 secs
Sep 14 21:40:28 ubuntu kernel: [   56.147357] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [   86.117887] ata3.00: qc timeout (cmd 0xec)
Sep 14 21:40:28 ubuntu kernel: [   86.117893] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 14 21:40:28 ubuntu kernel: [   86.117895] ata3: failed to recover some devices, retrying in 5 secs
Sep 14 21:40:28 ubuntu kernel: [   91.600501] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [  121.571032] ata3.00: qc timeout (cmd 0xec)
Sep 14 21:40:28 ubuntu kernel: [  121.571037] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 14 21:40:28 ubuntu kernel: [  121.571039] ata3: failed to recover some devices, retrying in 5 secs
Sep 14 21:40:28 ubuntu kernel: [  127.053645] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [  127.365338] ata4: SATA link down (SStatus 0 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [  127.840871] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [  157.811402] ata5.00: qc timeout (cmd 0xec)
Sep 14 21:40:28 ubuntu kernel: [  157.811407] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 14 21:40:28 ubuntu kernel: [  157.811409] ata5: failed to recover some devices, retrying in 5 secs
Sep 14 21:40:28 ubuntu kernel: [  163.294015] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 14 21:40:28 ubuntu kernel: [  193.264546] ata5.00: qc timeout (cmd 0xec)
Sep 14 21:40:28 ubuntu kernel: [  193.264551] ata5.00: failed to IDENTIFY (I/O error, err_mask=0x4)
Sep 14 21:40:28 ubuntu kernel: [  193.264553] ata5: failed to recover some devices, retrying in 5 secs
Sep 14 21:40:28 ubuntu kernel: [  198.385312] kjournald starting.  Commit interval 5 seconds
Sep 14 21:40:28 ubuntu kernel: [  198.385326] EXT3-fs: mounted filesystem with ordered data mode.
Sep 14 21:40:28 ubuntu kernel: [  198.747167] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)[/HTML]

What is a good way to respond to "Driver 'sd' needs updating - please use bus_type methods"?  and what do I do about "failed to IDENTIFY I/O error"?

Thanks,

 - Mike

---

