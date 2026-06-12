---
title: "Installing 64-bit to dual boot with 32-bit Ubuntu"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by ButtBuntu on 2013-01-30
Hi all, I currently have 32-bit Ubuntu 12.04 LTS running on my primary boot partition.  I installed 64-bit Ubuntu 12.04 LTS in another partition in hopes of running a dual boot setup.

After install, I was met with the same prompt that I am accustomed to for the 32-bit version.  The 64-bit partition was not showing up.  I believe I know what I did wrong here, but I'm looking for help to fix my error.

Here's how I installed the 64-bit version:

When I was prompted to create a new partition for the 64-bit version, I selected logical partition, ext4, 75000 MB, and mount from / as my variables.  I also selected to install boot from /sda5 (can't remember the exact wording but it was the pulldown menu on the bottom and the default selection was the whole 1 TB HD device...this may have been where I erred).

Any ideas on how I can get 64-bit partition to show up in the boot options?

fdisk info (* is my 32 bit version)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       268414976   272711663     2148344   82  Linux swap / Solaris
/dev/sda2   *   272711680   311771135    19529728   83  Linux
/dev/sda3       311773455   546306382   117266464   83  Linux
/dev/sda4       546308094   692791295    73241601    5  Extended
/dev/sda5       546308096   692791295    73241600   83  Linux

To summarize, just want to get /sda5 where 64-bit Ubuntu resides to show up in the boot menu.

---

### Post by ButtBuntu on 2013-01-30
SOLVED.  I loaded Boot Repair from a Live CD and simply switched the boot partition from /sda2 to /sda5.  You can lock this thread up!

---

### Post by Bucky Ball on 2013-01-30
> **ButtBuntu said:**
> SOLVED ... You can lock this thread up!

You can achieve this by using Thread Tools at top right and 'Mark this thread as Solved'. ;)

You could possibly have fixed this alternatively by booting into the install which was running the show with its grub and:

```
sudo update-grub
```

This would pick up any/all installs and add them to the menu.

---

