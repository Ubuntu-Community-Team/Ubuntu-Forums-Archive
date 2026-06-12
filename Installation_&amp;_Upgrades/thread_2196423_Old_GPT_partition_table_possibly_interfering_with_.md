---
title: "Old GPT partition table possibly interfering with new installation?"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by ejl389 on 2013-12-29
The story so far.

[LIST]
[*]Had issues with both OSes, tried to reinstall Ubuntu 
[*]Accidentally installed Ubuntu over Windows 7 
[*]Reinstalled Windows 7 
[*]Tried to reinstall Ubuntu 
[/LIST]

However, Ubuntu refused to acknowledge that there were any partitions on the drive at all, though I can verify that Windows is working perfectly. Thinking it was a problem with the installer, I attempted (and I believe I succeed) to set aside a 100 GB ext4 partition for Linux to live on. This was done under Windows. However, the Ubuntu installer is not recognizing this new partition either.

It's happened with multiple flash drives, 2 different live USB creators, 2 different flavours and a few different ISOs, so I dug a little deeper.

Output from sudo fdisk -lu:

```
root@it:/home/it# sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x270c8cd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1742575615   871184384    7  HPFS/NTFS/exFAT
/dev/sda3      1742575616  1953519615   105472000   83  Linux
```

Additionally, I can mount each of the latter two drives using a live session and examine their contents just fine.

The warning is reflected by GParted:

> /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by using a program that doesn't understand GPT partition tables. Or perhaps you deleted the GPT table, and are now using an msdos partition table. Is this a GPT partition table?

GParted also does not recognize that the disk contains any partitions. (I get this result whether I click Yes or No)

So it appears as though anything that can recognize GPT partitions tables thinks the disk is entirely empty. But being honest, I'm now more or less totally lost. Can anybody recommend a fix?

---

### Post by oldfred on 2013-12-29
If system was UEFI before then partitions were gpt. You can install Windows 7 in UEFI mode but have to copy to flash drive and make a few changes.
The default install of Windows 7 is BIOS based with MBR(msdos) partitions. But gpt has a backup partition table (one of its advantages), but Windows does not delete backup. So you have MBR with a backup gpt when any Linux tool looks at it and gets confused on which you really want. You have to choose.

If Windows is now BIOS, then you need to convert entire system to the 35 year old BIOS/MBR configuration which obviously is well known, but old. But need to remove backup gpt table.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Microsoft supposedly was encouraging vendors to not write drivers for new hardware for any older version of Windows, or to lock you into Windows 8. Most hardware has not yet changed enough that there are major issues now, but later there may be if upgrading your hardware.

---

### Post by ejl389 on 2013-12-29
Yep, fixparts did it. Thanks a bunch!

---

