---
title: "Adding Secondary Boot Drive Prevents Primary From Mounting?"
date: 2014-05-07
forum: Installation &amp; Upgrades
---

### Post by vnomus427 on 2014-05-07
Ok,  I'm probably showiing my Linux newibie-ness but I can't seem to get around this roadblock...I had two Ubuntu machines and one them died. I want to move it's two drives (HDD1 & HDD2) to the remaining machine but adding either prevents the exisiting boot drive (HDD0) from mounting. If I add the HDD1 boot drive then the system boots up, but off the HDD1 drive. If I add just the HDD2 drive then the machine drops me to a command prompt. I just want to use HDD1 & HDD2 as storage and keep the existing HDD0 as-is. I did update the boot order in the bios and even disabled booting from all but HDD0, still no joy. Removing the extra drives and the machine boots fine...

Any ideas on what I'm doing wrong?

Thanks in advanage for any and all help!....

---

### Post by oldfred on 2014-05-07
SATA drives or old PATA/IDE drives?

If older drives are jumpers set correct for master/slave or cable select? And then are you using a 80 conductor PATA cable not the old 40 conductor cable that only works with master/slave? The 80 conductor has 3 different colors for connectors.

Is BIOS showing all three drives correctly?

Post this from any working Ubuntu or live installer.
sudo parted -l

---

### Post by vnomus427 on 2014-05-08
oldfred, first off thank you for the reply!...
The drives are both 1TB SATA and yes the bios recognized all three. I am able to get them to work if I first boot the machine with just HDD0 and then hook them up. I used the Disks applet to repartition HDD1 to just a single data drive and tried to reboot unfortunatley now it just goes into aninfinite boot cycle. 
Here's the output (with the drives hooked up after boot)

Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  992GB   992GB   primary   ext4            boot
 2      992GB   1000GB  8536MB  extended
 5      992GB   1000GB  8536MB  logical   linux-swap(v1)


Model: ATA TOSHIBA DT01ACA1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  1000GB  1000GB  primary  ext4


Model: ATA WDC WD10EZEX-08M (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1000GB  1000GB  ext4

---

### Post by oldfred on 2014-05-08
sdc: Partition Table: loop
That says the drive is not partitioned. Back up any data you have and partition drive. A few have used formatted drives without partitions and had major issues.

If it is trying to boot from sdc or even check if sdc is bootable that may be part of the issue as it has no MBR for boot code.

---

### Post by vnomus427 on 2014-05-09
> **oldfred said:**
> sdc: Partition Table: loop
That says the drive is not partitioned. Back up any data you have and partition drive. A few have used formatted drives without partitions and had major issues.

If it is trying to boot from sdc or even check if sdc is bootable that may be part of the issue as it has no MBR for boot code.


I ran bootfix on it and it warned that the boot partition wan't close to the start of the disk and that the bios might not be able to detect it. Not sure why it was partitioned like that in the first place but it was originally running Win8 so that may be related. Anyway I ended up just re-installing from scratch, with the extra drives installed, and everything seems to be working now. Thanks again for your help!....

---

