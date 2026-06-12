---
title: "Partition structure: Tri-boot with Windows, Ubuntu and Mint"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2017-11-05
Very simple question:

Suppose I want to tripple-boot Windows, Ubuntu and some other Linux distro on a single disk, what's the "recommended" or "ideal" partition table setup? Create a 'Primary' partition for both Ubuntu and Mint, a 'Logical' partition for both Ubuntu and Mint, or a 'Primary' for Ubuntu and 'Logical' for Mint or vice-versa?

PS: I know there isn't a "proper" way to do this, but since I'm no expert there may be something I'm missing out about partition structuring etc.

---

### Post by Dennis N on 2017-11-05
If you are going to create a new partition table, I would use GPT partitioning for the disk. Then all partitions are the same type. There are no logical partitions on a GPT partitioned disk, and you have by default 128 of them.

---

### Post by ajgreeny on 2017-11-05
I am presuming this will be a new, clean install of all three or more OSs, and if so I would also suggest you use GPT partitions.

Does your computer have a UEFI option, as may also give you another choice, UEFI or BIOS, though if you use GPT you will probably have to use UEFI for Windows, (though that may depend on the Windows version) and if Windows has to be UEFI so will your Linux OSs or you will have big boot problems.

---

### Post by oldfred on 2017-11-05
Is this a newer UEFI hardware based system?
Windows only boots in UEFI mode from gpt.
Ubuntu can boot in UEFI or BIOS if you have correct supporting partitions.

Windows if BIOS/MBR has to boot from a primary partition.
Linux can boot from logical partitions just as well.

I might have a shared NTFS data partition for any data you might want in all 3 systems. But if Windows 8 or 10 you must have the fast start up or always on hibernation off, or the NTFS data partition is also hibernated and not read/write from Linux.

 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

