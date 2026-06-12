---
title: "Post Mortem: A Dual Booting Odyssey"
date: 2005-02-22
forum: Installation &amp; Upgrades
---

### Post by wheatpuppet on 2005-02-22
I figured I'd share how I set up a dual-boot setup for Windows XP Professional x64 Edition (beta) and Ubuntu 4.10, since other people may want to try something similar and there are a number of places where I got tripped up. This is an install from nothing, so if you want to retain your current WinXP-64 installation, I don't know how much this is going to help.

First, pop in the Ubuntu install disk and follow the appropriate menu prompts until the dialog box labelled "[!!] Partition disks". 

Here there are two options, first is to delete the entire disk, second is to manually edit the partition table. Select the second option, since we want to set up some partitions to stick our operating systems in.

Using the partitioning tool, create a new partition at the beginning of the unallocated space and set it to use NTFS. Leave the rest of the space unallocated.

Select "Write Changes to Disk" and find an appropriate point to swap your CD with the Windows XP-64 disk and reboot.

Follow the on-screen instructions for installing Windows XP-64, and install Windows XP in the partition you made. I personally don't trust the WinXP installer  to do the partitioning, hence the pre-partitioning using the Ubuntu disk. Fully install Windows (which takes one or two reboots, IIRC), then put the Ubuntu disk back in.

Follow the on-screen dialog boxes again until you reach "[!!] Partition disks". At this point you want to select the unallocated space and partition it into two sections, a large ext3 partition containing your Ubuntu install, and a smaller fat32 section that will allow you to pass files between your OSes (I mounted it as /shared). I'm planning to put all my music there, for instance. Unfortunately, I discovered that I can't just put /home on that partition because of some sort of read-write problem.

Other guides will tell you that Windows will be detected when GRUB is installing itself. It does **not** detect Windows XP 64-bit edition. Perhaps becuase it's a beta version of windows. In any case, GRUB will install itself completely ignorant of Windows. This is okay, for now.

Follow the on screen instructions for the Ubuntu installation. When it's done, login as whatever your username is, and immediately open a terminal. Type:

sudo pico /etc/grub/menu.lst (substitute pico for your favorite text editor)

Scroll down until you see a bunch of lines like this:
title Ubuntu (kernel)
...

title Ubuntu 64-bit
...

And add to the end:

title Windows XP-64
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

You might want to change the line labeled "Timeout" to something more reasonable (10 seconds is fine for me) and comment-out the line labeled MenuHide (or somesuch). This will give you the option to boot into WinXP-64.

---

