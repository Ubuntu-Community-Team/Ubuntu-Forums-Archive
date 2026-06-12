---
title: "Dual boot and partitioning tips, part 2"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by mike_f on 2008-08-21
I've discovered a few more pecularities of partitioning utilities since [my last post]("http://ubuntuforums.org/showthread.php?t=367110") (which I can no longer edit). Hopefully this one will be editable for a while.

- Get the [System Rescue CD]("http://www.sysresccd.org/").
This LiveCD distro has gone gold, now v1.0.4. It has a wealth of helpful programs including gparted, testdisk, clamav and all of the usual Linux command line utilities.

- Partition your drive *before* installing Linux or Windows, then tell the installer which partition to use (Manual option in Ubuntu install). I've been burned too many times by (non-Ubuntu) installs that screw up partitioning.

- When partitioning a new drive, create all four primary partitions; the last one should be an 'extended' one which can contain multiple logical partitions.
When you delete and add partitions this may cause the 'out of order' condition that some Linux utilities report. This may explain why sometimes gparted just locks up, or not. A good practice is to resize previously created primary partitions. FYI Partition Magic (DOS/Windows based) always shows partitions in physical order, no matter what order they show up in the master boot record (MBR) partition table.

- Create a separate logical partition formatted NTFS for sharing data between Linux and Windows.
Ubuntu mounts NTFS partitions writable by any user by default, no fstab futzing needed. If you are using Windows, *always* create a logical partition for personal data files; this makes data backup and Windows reinstallation easier. Windows users should move their 'My Documents' folder to that drive letter (logical partition).

- If you are adding a second data drive and using PM, create three small (8Mb) primary partitions and an extended one to contain all of your data partitions. PM usually will NOT work on a disk with only an extended partition on it.

- Use [grub4DOS]("http://grub4dos.sourceforge.net/") and  [FreeDos]("http://www.freedos.org/") as the 'master' boot manager, then install grub in the *partition* boot record during Linux installation.
DOS based programs are quick to (re)install in case of trouble. Set up the grub4DOS menu (menu.lst file) to 'chainload' to all bootable OS's; Windows always installs with its own crippled boot manager (controlled by boot.ini) in the partition boot record (PBR) even if its menu isn't displayed. Use the freeware version of aefdisk to write a plain MBR if needed (can't recall the best alternative on the SysRescue CD).

More to come ???

---

