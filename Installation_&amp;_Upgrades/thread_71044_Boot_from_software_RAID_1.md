---
title: "Boot from software RAID 1"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by kdvgent on 2005-10-02
I searched a bit on the forums but did not find much information.  So I decided to describe how I made it work (on the 5.10 preview hence this is maybe not the best place to post but I do not find a better one).
I have some experience with gentoo and used this experience to install Ubuntu with software raid (including for boot)
I have two identical disks, both with 4 partitions: boot (raid1), swap (raid0), root (raid 1) and the rest (raid1, lvm and then separate partitions for usr, home, opt, var and tmp).  Boot is ext, root and the rest are Reiser.  All partitioning done during the partitioning phase of the install process.  For installation, I installed the raid1 partitions with one active disk and one spare disk.  I finalised the installation, used it for a couple of days to be sure it worked.
Then I made the spare disks in the raid1 arrays active.  This cannot be done while the partitions are mounted, hence I had to boot from a live version of the preview and use evmsn to find the raid1 arrays and instruct that the spare disks be converted to active ones (a process that takes around 1.5 days for my 150 GB disks).
Finally, I edited the /boot/grub/menu.lst: copied all menu items, changing hd0 in hd1.  And, using the "grub" command itself, I installed the necessary software in the MBR of both disks:
> root (hd0,0)
> setup (hd0)
> root (hd1,0)
> setup (hd1)
And it all seems to work (I can boot from both disks).
I have only little problem where I could use some help: is there a way to tell the system - via the AUTOMAGIC KERNEL LIST feature - that in menu.lst also the entries pointing to the second disk must be upgraded every time there is a kernel upgrade?  Or should I do this manually after each kernel upgrade.
Hope this may be of help for some.

---

### Post by DJ_Max on 2005-10-02
Thanks for sharing your experience.

Have you tried the wiki? [https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)
There's something similar, [https://wiki.ubuntu.com/Installation/RAID1](https://wiki.ubuntu.com/Installation/RAID1)

---

