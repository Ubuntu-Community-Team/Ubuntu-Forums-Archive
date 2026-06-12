---
title: "Installation uses fdisk or gdisk depending on hardware?"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by hanslammerts on 2011-06-25
Hello again,
 
Just noticed something strange.
I have installed 10.04 64bit on two machines that have different hardware.
After the installation (that went perfectly by the way), I needed to add extra
partitions on both machines. Normally I use fdisk for this, and on one machine this went OK. On the second machine, however, after starting fdisk, I got the warning message that a GUID Partition Table was found on the disk, and fdisk was not compatible.
This leads me to believe that during installation on the first machine fdisk was used to partition my harddisk, and on the second machine gdisk or gparted was used.
 
Is this normal ?
Is there a way at installation time to force the use of fdisk ?
 
Hope someone knows the answer to this.
 
Thanks,
Hans

---

### Post by srs5694 on 2011-06-25
The Ubuntu installer uses neither fdisk nor gdisk; it uses a partitioning tool based on libparted, which is the core of GNU Parted, GParted, Palimpsest Disk Utility, and other tools. You can use fdisk to manipulate Master Boot Record (MBR) partitions and a few other obscure partition types; gdisk to manipulate GUID Partition Table (GPT) partitions and to translate between GPT and MBR; and libparted to handle (but not translate between) various partition table types, including both MBR and GPT.

I don't know the exact rules that the Ubuntu installer uses to decide which partition table type to use, but I believe the following to be true:


[list]
[*]If a disk has an existing partition table, the installer uses it rather than creating a new one; it creates a new table only if the disk has none, or possibly if you to tell it to wipe the disk clean (I've not checked this last detail).
[*]If the computer uses (U)EFI firmware, the installer uses GPT when it creates a new partition table.
[*]If the disk is over a certain size (something between 1TB and 2TB), the installer uses GPT when it creates a new partition table.
[*]If the disk is under that size *and* the computer uses BIOS firmware, the installer uses MBR when it creates a new partition table.
[/list]


Thus, my suspicion is that your GPT-using computer already had a disk with GPT partitions, had a disk that was over 1TB in size, or was based on UEFI. Depending on which of those was the case, and perhaps more precise details, you might or might not want to override the decision to use GPT. For instance, MBR is inadequate for disks of over 2 TiB, so if you've got a 3 TB disk or a RAID array of over 2 TiB, you pretty much have to use GPT to use the whole disk. (There are some risky ways to use MBR for disks of up to 4 TiB, but I recommend against their use.)

Even on sub-2TiB disks, GPT has some advantages over MBR, such as no distinction between primary, extended, and logical partitions; a backup of partition data on the disk; CRCs of partition data that can help spot errors; labels for partitions; and no more use of CHS addressing (except in the protective MBR). Thus, for a Linux-only installation, IMHO GPT is a superior partitioning system to MBR. The biggest advantage of MBR is in compatibility with a wide variety of OSes. Windows, in particular, can boot from GPT disks only on UEFI-based computers, so MBR is the better choice on a dual-boot BIOS-based computer. (On UEFI, though, Windows is equally wed to GPT.)

If you really want to use MBR rather than GPT, you can probably do so by setting the disk up in MBR before installing Ubuntu. You might not even need to create partitions, just set up the basic MBR structures. If the disk already has GPT data, though, you've got to do this with a utility that understands GPT at least well enough to wipe the old GPT data. If you don't do that, libparted-based tools get confused and tend to report the disk as unused, or sometimes they use the old GPT data rather than the new MBR data.

---

