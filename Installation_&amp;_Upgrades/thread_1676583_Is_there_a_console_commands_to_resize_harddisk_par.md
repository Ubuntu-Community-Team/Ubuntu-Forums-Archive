---
title: "Is there a console commands to resize harddisk partition ?"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-01-27
I want to resize my harddisk partition to make it bigger is there a console commands to do this ?
I have some free harddisk that I want to ubuntu to use, I have hear that one can use Gpart, but is it also possible achieve the same by using some commands ?

---

### Post by Rubi1200 on 2011-01-27
What file-system type are you currently using on the drive?

To be honest, GParted is so easy to use, why do you want/need to do it via the CLI?

---

### Post by hoboy on 2011-01-27
> **Rubi1200 said:**
> What file-system type are you currently using on the drive?

To be honest, GParted is so easy to use, why do you want/need to do it via the CLI?

I have never sue Gparted maybe I should give a try.

---

### Post by weedeater64 on 2011-01-27
fdisk

---

### Post by srs5694 on 2011-01-27
As Rubi1200 suggests, GParted is the easiest way to do this.

If you can't use a GUI, the GNU Parted program (command name "parted") can do the same job. It's an interactive tool; type "sudo parted /dev/sda" (or whatever the disk is) to get to a "(parted)" prompt and type commands at that prompt. It's also possible to issue command-line commands "e.g., "sudo parted /dev/sda print".

The fdisk program can alter *partition* data structures, but it won't touch the *filesystem* data structures inside the partitions. Thus, to do any good, you must use filesystem-specific resizing tools, such as resize2fs, to do a complete job. If you're shrinking a partition, you'd use resize2fs first, followed by fdisk; if you're increasing a partition's size, you'd use fdisk followed by resize2fs. If you need to change the start point of a partition, it gets ugly.

Depending on what you need to do, you might need to boot from an emergency disc to do this work; you may not be able to resize partitions or filesystems that are in use.

---

