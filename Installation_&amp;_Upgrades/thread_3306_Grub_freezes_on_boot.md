---
title: "Grub freezes on boot"
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by risager on 2004-11-05
Hi, 

I just installed Ubuntu on my Toshiba M35-s456 laptop. I hope to dualboot with Win XP. Grub was installed to the MBR on my 80 GIG harddrive.

When I start the computer I see GRUB in the upper left corner. And thats it. It freezes right there. Any pointers to help me in the right direction

Morten

Disk /dev/hda: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       51096    25752163+   7  HPFS/NTFS
/dev/hda2   *       51097      153856    51791040   83  Linux
/dev/hda3          153857      154848      499968    f  W95 Ext'd (LBA)
/dev/hda5          153857      154848      499936+  82  Linux swap
--------------------------
device.map
(hd0) /dev/hda
----------
menu.lst at [http://home.imf.au.dk/risager/menu.lst](http://home.imf.au.dk/risager/menu.lst)

---

### Post by cutlassdude70 on 2005-03-29
I also have a M35-S456 and am having the exact same problem with GRUB (but installing Gentoo though).  I have a feeling it is related to how the BIOS is looking at the hard drive (i.e. NORMAL vs LBA mode), but the BIOS has no hard drive options (even after upgrading to Phoenix BIOS 1.30).  Any help would be GREATLY appreciated.

---

### Post by frozenjim on 2006-02-12
Toshiba M30

I have gone through a complete installation three times.  Each time with the same result:  I reboot and see the word GRUB in the top left corner of the screen.  It is NOT the grub prompt, it is just the word GRUB.  Press any key 15 times and the keyboard buffer fills.  So it is locked solid.  Grub just won't load.

I have tried almost every kernel switch that I can in my grub file, but nothing makes any difference.

Sadly, Toshiba doesn't give you access to much by way of a BIOS.

Has anyone had any luck yet?

[edit]
Wow.  I booted from the Toshiba recovery CD.  It recreated all partitions and did a full install.  Then I rebooted and guess what?  THE SAME GRUB IN THE TOP LEFT CORNER.

Also, I had booted with my Knoppix LiveCD and ran QTParted which noticed that my /dev/hda1 partition did not extend to the beginning of the CD.  It also noticed an error in my partitioning scheme - one of my partitions extended past the end of my hard disk (which is odd because the second half of my disk was all unpartitioned space).

So I'm wondering if things screwed up when I used Partition Magic BEFORE installing Linux.

I will boot now from a Windows XP CD (not recovery CD) and try running fixmbr.  I'll edit this note to let you know how it works out.

[edit]

Well, fixmbr worked to get Windows running again.

I repartitioned again and installed Windows using my recovery CD (ghosted).  Then I resized my partition and added a couple more for Linux.  This time, I put grub on /dev/hda2 and set it bootable.  Did a normal Linux install and rebooted.

No good.  I got the same GRUB in the top left corner of the screen.  

Switched /dev/hda1 back to bootable, thinking that I could load Windows at least, but no.  This time fixmbr didn't work either, nor did fixboot.  I get a Windows error "Error loading operating system".

So I'm stumped.  If I find a solution I will revisit this thread and let you know what it is.  I have a bug in with Grub, but it's been a week with no reply so I'm not hopeful.

---

### Post by madscience on 2006-07-24
The solution to this issue is to remove the 'Express Media Player' partition using the separate restore disc for the software.  This software uses a 'Host Protected Area' on the HDD, which conflicts with GRUB.

---

### Post by jzimmerman on 2006-10-22
[http://wiki.linuxquestions.org/wiki/Dual_booting](http://wiki.linuxquestions.org/wiki/Dual_booting)

The above link will describe how to use the NT Boot Loader to start grub.

This is assuming you are going to keep the Windows XP / 2K installation on the primary partition.

You do not need to remove the Express Media player to do this.

I am running Windows XP, Ubuntu, and Express Media Player just fine on my M35-S456 Toshiba.

So the boot process would look something like this to boot into linux when you are done (you will need to use the rescue option to set it up though).

BIOS -> MBR -> NTLOADER/BOOT.INI -> select Linux to load grub -> select your kernel

To boot Windows just choose the windows option from the NTLOADER screen.

---

