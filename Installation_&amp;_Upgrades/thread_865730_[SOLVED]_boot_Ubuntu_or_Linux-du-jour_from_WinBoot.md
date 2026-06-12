---
title: "[SOLVED] boot Ubuntu or Linux-du-jour from WinBoot menu"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by rated727 on 2008-07-20
Thanks for following your curiosity to check this thread.  I'll admit from the start that I want to do something that is quite outside the norm, for reasons that may make sense only to me.

Briefly the situation is as follows:

One hard drive (HD0) - 4 partitions
...NTFS partition, WindowsXP
...EXT3 partition, Ubuntu
...EXT3 partition, some other Linux distro
...Linux swap partition

Today's goal: __ To pass load control from Windows Boot Menu to GRUB (installed on the first EXT3 parttion) which will load and start Ubuntu ...OR... pass load control to GRUB or LILO (on second EXT3 partiton) to load the Linux distro that I am test-driving this week.

The purpose: __ to create a virtual MBR on each EXT3 partition and thus avoid having to fix such problems as having LILO trash GRUB and the HD0 MBR.

Does anyone feel creative?  Does anyone question my motives? Does everyone question my sanity?
(the answer to the 3rd question above is usually "Duhhhh", but your milage may vary ;)

"If my computers didn't occasionally 'self-destruct' what would I do for entertainment?" -- rated727

---

### Post by louieb on 2008-07-21
piece of cake. Each partition has a boot sector.  You can install GRUB or LILO in a partitions boot sector. And then to start the boot loader on that partition you chainload from whatever boots off the MBR.  More here just search for chainload on this page. [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by logos34 on 2008-07-21
It's easier to use grub as the master dual boot loader, but if you want to use windows bootloader, as the thread title says, to chainload ubuntu grub with the further option of loading a second linux on sda3, try this:

1. Write ubuntu grub to the root partition:
[B]
sudo grub-install /dev/sda2[/B]

2. Copy the first sector of root partition to the windows C:\ drive (sda1) and edit **boot.ini** file:
[B]
sudo dd if=/dev/sda2 of=grub.mbr bs=512 count=1
[/B]
Look for 'grub.mbr' in home dir and copy to windows C:\  

Add this line to boot.ini:

> c:\grub.mbr="Ubuntu 8.04"(Note: if editing the file in windows, it's hidden so either type 'boot.ini' in the explorer address bar or Start>run>msconfig>BOOT.INI tab)

Do # 1 for the new linux as well.

Then add a [configfile, chainloader, or symlink]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems") entry to ubuntu menu.lst.

So you boot and are given a choice of windows or ubuntu.  You choose ubuntu and are then greeted by the menu.lst list where you have a choice of ubuntu or the other linux flavor on sda3.

---

### Post by rated727 on 2008-07-30
Thanks, you provided a perfect working solution to my request and some good links.  'Grub Page' is especially interesting and educational ... and that's a good thing.

---

