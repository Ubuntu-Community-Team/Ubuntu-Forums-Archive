---
title: "Resizing root and home partitions. Will grub make it work afterwards?"
date: 2022-04-15
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2022-04-15
I am going to shrink my root partition and expand my home partition. I plan on doing this with Gparted.

After I do this, I expect to reinstall Grub with boot-repair. Can I expect that the system will recognize the home partition and it will boot okay?

---

### Post by tea for one on 2022-04-15
If this is a UEFI mode system, then Grub will be OK and boot-repair should not be needed.

Before you attempt this, make sure that you have backed up your personal data.

---

### Post by robertcull1 on 2022-04-15
I'm running a BIOS system.

I'll be cloning my drive and seeing if I can resize the clone first.

---

### Post by ubfan1 on 2022-04-15
gparted should run the resize2fs, so the UUIDs will be changed on the filesystems.  sudo update-grub should be all that's needed to rewrite the grub.cfg file with the new UUIDs.

---

### Post by grahammechanical on 2022-04-15
I have resized partitions many times on a BIOS motherboard system and I have never needed to use Boot Repair to re-install Grub. Does the hard drive have Master Boot Record (MBR) partitioning scheme? In this situation Grub is installed in the Master Boot Record (MBR) at the front of the drive. There should always be about 2 MB unallocated space before the first partition.

We can have a drive with the GPT (GUID Partition Table) with a BIOS motherboard. The Ubuntu installer will create two partitions in addition to the Ubuntu partitions. There will be a Bios boot partition and an EFI system partition. Provided we do not mess with either of them then resizing partitions should not effect the Grub booting process.

Regards

---

### Post by TheFu on 2022-04-15
If the UUIDs change, then the fstab will need to be modified for the new UUID values.  That can be done from a Try Ubuntu environment with any flash install drive.  If you are comfortable with blkid, lsblk and how the fstab works, this is very easy.

---

