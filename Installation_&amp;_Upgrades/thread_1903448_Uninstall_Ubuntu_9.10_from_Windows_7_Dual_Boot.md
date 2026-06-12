---
title: "Uninstall Ubuntu 9.10 from Windows 7 Dual Boot"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by Marionumber1 on 2012-01-02
I've messed up the Ubuntu installation I have, and considering I wasn't using it that often, decided to remove it. But I have a few questions about it:

First, my partition layout:

/dev/sda1: Windows Vista (has non working installation, primary)
/dev/sda2: Windows 7 (main OS, primary)
/dev/sda3: FreeDOS (primary)
/dev/sda4: Extended Partition (extended)
    /dev/sda5: Ubuntu (logical)
    /dev/sda6: Data (holds the Users folder for Win7, E: drive in Win7, /dev/sda2 has a junction to the data on this drive, logical)
    /dev/sda7: Swap Partition (logical)

So does the uninstall go like this?

1. Reinstall the Windows 7 bootloader to the MBR with EasyBCD.
2. Delete the Ubuntu and Swap partitions.

Assuming that I use EasyBCD to reinstall the Win7 bootloader, do I need to make a new entry for Windows 7 before installing its bootloader to the MBR?

And when I remove the partitions, will /dev/sda6 still be the E: drive?

---

### Post by searchfgold6789 on 2012-01-02
> So does the uninstall go like this?

1. Reinstall the Windows 7 bootloader to the MBR with EasyBCD.
2. Delete the Ubuntu and Swap partitions.No. First delete the partitions, then write the MBR.
> And when I remove the partitions, will /dev/sda6 still be the E: drive? 	Yes. And you can resize the partition to fill the extended area if you want.

---

### Post by darkod on 2012-01-02
I would agree with first making win7 boot with the windows bootloader, and then deleting the ubuntu partition when win7 is working OK. You can keep the partition as long as you want.
The main issue is not to leave the system unbootable.

You can also restore the windows bootloader with the win7 dvd (if you have it), by booting with it and doing the Repair This Computer procedure. Sometimes you need it 2 or 3 times.

---

### Post by Marionumber1 on 2012-01-02
But can I just go to EasyBCD and click write to MBR, or do I have to add a Windows 7 entry first?

---

### Post by Mark Phelps on 2012-01-02
> **Marionumber1 said:**
> But can I just go to EasyBCD and click write to MBR, or do I have to add a Windows 7 entry first?

You can just click the Write MBR button -- and it will rewrite the MBR.  You don't need to add any other entries.

---

### Post by Marionumber1 on 2012-01-02
One thing I forgot to add, can I then move /dev/sda6 out of the extended partition and make it primary?

---

### Post by darkod on 2012-01-02
I wouldn't touch it. Any partition moves are risk to your data if things go bad so avoid everything that is not necessary.
Plus, according to your first post, if you make it primary it will be fourth, which means you will not be able to create any more partitions in the future. If you keep it logical, you can still create another partition if needed some day.

---

### Post by darkomano on 2012-01-03
You could ( when booted to Windows 7 ) run "Dual-boot Repair" -> "Automatic Repair"
 
The tool will write a new Windows 7 MBR and create or repair (on active partition) Windows 7 boot environment = PartitionBootRecord + bootmgr + \boot folder with BCD in it.
Windows 7 will be the default system to boot.
 
**Do not move or resize partitions that are placed physically in front of active and active partition itself as this will create boot problems !**
 
**It is best if active partition is the first primary partition on disk (and first physical partition) - Windows 7 install to unformated disk always creates a "System Reserved" 100 MB primary active partition. The reason is to be prepared for encryption (of system partition) and multi-booting of other OS !**
 
[Download link]("http://www.boyans.net")

---

### Post by Mark Phelps on 2012-01-04
> **Marionumber1 said:**
> One thing I forgot to add, can I then move /dev/sda6 out of the extended partition and make it primary?

NO -- you already have the maximum of three Primary partitions and one Extended partition.

---

### Post by Marionumber1 on 2012-01-07
When I said move /dev/sda6 out of the extended partition, I meant after removing FreeDOS. And I never actually had a System Reserved Partition. I have a Partition Boot Record on the Windows 7 partition.

---

