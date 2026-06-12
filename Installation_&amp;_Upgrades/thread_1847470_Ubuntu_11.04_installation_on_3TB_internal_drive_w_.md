---
title: "Ubuntu 11.04 installation on 3TB internal drive w/ bootup errors"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by razor_maze on 2011-09-20
I'm having problems getting a clean boot with Ubuntu 11.04 64 bit version.  Here are some of the details and the boot-up errors I'm getting.  If anyone knows what's going on, I'd appreciate some advise.

Hardware details:
Motherboard: GIGABYTE GA-X58A-UD3R
Chip: Intel i7-960
Harddrive: Hitachi 3TB SATA 6 Gb/s

At boot-up:
Verifying DMI Pool Data..................
error: out of disk
error: no suitable mode found
error: no video mode activated
error: out of disk

After that, the system seems to go into a normal boot sequence.  Does anyone know what's going on?

---

### Post by srs5694 on 2011-09-20
First, if by "the system seems to go into a normal boot sequence" you mean that it boots normally, it might not be a real problem, just a confusing message. OTOH, if you're saying that Linux isn't booting, then that's obviously a problem.

I've checked the manual for your motherboard, and I didn't find any mention of EFI or UEFI firmware, so it appears to be a normal BIOS-based computer. This is critical because it means you're limited to BIOS boot loaders. Some of these, on at least some computers, have limits of 2 TiB, 1 TiB, or even lower for where boot files must reside. This means that if you just partitioned your 3 TB disk using default options in the Ubuntu installer, you could easily end up with the Linux kernel or other files above the BIOS's and/or boot loader's read limits, which could prevent the computer from booting.

On a 3 TB disk, you'll also almost certainly need to use the GUID Partition Table (GPT) partitioning scheme rather than the older Master Boot Record (MBR) partitioning scheme. This is important because if you use GRUB 2 with GPT, creating a [BIOS Boot Partition](http://en.wikipedia.org/wiki/BIOS_Boot_partition) is desirable. This is a partition in which GRUB 2 stores part of its boot code. (On MBR disks, this code normally goes in officially-unallocated sectors near the start of the disk.)

Combining these factors, you should do the following to ensure that the disk will be bootable on your computer:


[list]
[*]Use GPT, not MBR. The Ubuntu installer will do this automatically if the disk is completely empty.
[*]Create a BIOS Boot Partition early on the disk -- say, as the first partition. It can be just 1 MiB in size, or even less (in theory, something as small as about 30 KiB is adequate, but 1 MiB is good because of partition alignment issues).
[*]Create a separate /boot partition just after the BIOS Boot Partition. This should be about 200-500 MiB in size. Personally, I'd make it ext2fs, since a journal won't speed up disk checks all that much on such a small partition, and the space a journal consumes will be missed more on such a small partition compared to a big one. You can use another filesystem if you prefer, though.
[/list]


If there are any other relevant facts about this system, please post them now. For instance, if you're currently or plan to dual-boot with Windows, that's extremely important. If you need more help, please boot the Ubuntu installer into its "try it now" mode, open a Terminal window, and type:

```

sudo parted /dev/sda unit s print

```

This should produce relevant information about your partitions. Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.

---

