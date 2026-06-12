---
title: "Ubuntu 8.04 Raid 1 Failure"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by dinkoarun on 2013-03-20
I am having a Ubuntu 8.04 LTS server installed with Raid 1 partition.

I have two raid partitions:

> /dev/md0
/dev/md1

In both the raid partitions I had two hard drives:

> /dev/sda1 and /dev/sdb1
/dev/sda2 and /dev/sdb2 

Since yesterday the device /dev/sdb1 and /dev/sdb2 has failed and is not showing up when I run **fdisk -l**

In the syslog I getting the following error:

> ata1: port is slow to respond, please be patient (Status 0x80)
ata1: softreset failed (device not ready)
ata1: port is slow to respond, please be patient (Status 0x80)
ata1: softreset failed (device not ready)
ata1: port is slow to respond, please be patient (Status 0x80)
ata1: softreset failed (device not ready)
ata1: limiting SATA link speed to 1.5 Gbps
ata1: softreset failed (device not ready)
ata1: reset failed, giving up
ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata2.00: ATA-7: WDC WD2500YS-23SHB0, 20.06C04, max UDMA/133
ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
ata2.00: configured for UDMA/133
ata3: SATA link down (SStatus 0 SControl 300)
ata4: SATA link down (SStatus 0 SControl 300)
ata5: SATA link down (SStatus 0 SControl 300)
ata6: SATA link down (SStatus 0 SControl 300)
scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500YS-23S 20.0 PQ: 0 ANSI: 5
ata_piix 0000:00:1f.1: version 2.12
ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 16 (level, low) -> IRQ 17
PCI: Setting latency timer of device 0000:00:1f.1 to 64
scsi6 : ata_piix
scsi7 : ata_piix
ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18c0 irq 14
ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18c8 irq 15
Driver 'sd' needs updating - please use bus_type methods
ata1: exception Emask 0x10 SAct 0x0 SErr 0x4080000 action 0xa frozen
ata1: irq_stat 0x00000040, connection status changed
ata1: SError: { 10B8B DevExch }
ata1: hard resetting link
sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 1:0:0:0: [sda] Write Protect is off
sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
sd 1:0:0:0: [sda] Write Protect is off
sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sda: sda1 sda2
sd 1:0:0:0: [sda] Attached SCSI disk
sd 1:0:0:0: Attached scsi generic sg0 type 0
md: md0 stopped.
md: bind<sda1>
raid1: raid set md0 active with 1 out of 2 mirrors
md: md1 stopped.
md: md1 stopped.
md: bind<sda2>
raid1: raid set md1 active with 1 out of 2 mirrors

Is it possible for me to re-add the device /dev/sdb back into the raid without replacing the hard drive?

If I have to replace, can I just buy a new hard drive and replace it with a old like a hot swap?

I need advice, please help!!

---

### Post by darkod on 2013-03-20
If the disk has failed there is no way to use the same one. You can try investigating if it's the disk or not, but if fdisk and parted don't show it, I guess that means it's failed/dead.

You would have to buy a new disk (brand new or second hand, doesn't matter), and replace the failed one. The procedure would involve something like:
1. Fail the disk in the mdadm devices with the --fail option.
2. Remove the disk/partitions from the array(s).
3. Power down the server and replace the physical disks.
4. Power on and partition the new disk with partitions of the same or greater size than the old ones.
5. Add these two partitions to the correct md devices and let it sync.

That's it.

---

### Post by dinkoarun on 2013-03-20
Thanks for the reply Darkod.

When I run the **cat /proc/mdstat** command, I get the following results:

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[1]
      9727232 blocks [2/1] [_U]

md0 : active raid1 sda1[1]
      234468544 blocks [2/1] [_U]

Also, this is what I get when I run the following command:
**sudo mdadm --query --detail /dev/md0**

> /dev/md0:
        Version : 00.90.03
  Creation Time : Sat Nov  8 17:15:25 2008
     Raid Level : raid1
     Array Size : 234468544 (223.61 GiB 240.10 GB)
  Used Dev Size : 234468544 (223.61 GiB 240.10 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Mar 21 01:45:56 2013
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 71d81ca7:3ff3552f:e05a9eec:5a6d8245
         Events : 0.45037125

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        1        1      active sync   /dev/sda1

So I guess the device /dev/sdb1 is already removed from the array. So is there no need to run the fail and remove command?

Also, when I get the new hard drive these are the following commands I am planning to run:

> sfdisk -d /dev/sda | sfdisk /dev/sdb
mdadm --manage /dev/md0 --add /dev/sdb1
mdadm --manage /dev/md1 --add /dev/sdb2 

Please let me know if the steps are correct, or am I missing something.

---

### Post by darkod on 2013-03-20
They are correct, but I personally don't like using sfdisk to copy the partition table especially if the disks are not identical. Imagine if you get much bigger disk now, the partitions will still be the small size. It's true that even if you make bigger partitions you will not be able to use all of it because the smaller partitions of sda will limit the mdadm array size, but at least sdb will be added with bigger partitions. If in future you replace sda even if it doesn't fail, you will be able to take advantage of the bigger partitions right away without repartitioning. I don't you will be able to do that if you use sfdisk.

I would make the partitions on sdb manually with parted and then run the mdadm commands. Just my preference.

---

