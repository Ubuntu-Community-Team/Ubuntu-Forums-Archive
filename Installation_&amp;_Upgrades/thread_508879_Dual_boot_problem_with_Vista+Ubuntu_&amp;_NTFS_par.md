---
title: "Dual boot problem with Vista+Ubuntu &amp; NTFS partition lost"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by daisyzss on 2007-07-24
I bought a PC with Vista installed. Then, I followed the steps for the dual boot Vista+Ubuntu from some website.  Ubuntu experience is exciting. But the problem is my previous Vista never boot again. 

I checked my partitions which shows below:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          62      497983+  82  Linux swap / Solaris
/dev/sda2              63        1278     9767520   83  Linux
/dev/sda3   *        1279        3710    19535040   83  Linux

The 204GB NTFS  partions never shows up!!!
Then, I use GParted to check the disk information. It shows the 204GB partitions as the unallocated. I modified the menu.lst. It doesn't work at all. I guess I overwrote the NTFS disk. But, why it is shown as the unallocated one? And, can I get that part back and do dual boot Vista+Ubuntu again without re-installing Vista?

Thank you!

---

### Post by Pumalite on 2007-07-24
You could try first your Vista CD and go to Recovery>FIXMBR ( I'm only guessing here that Vista has Recovery as XP did ). That way you'll see if you still have Vista. You could then reinstall Grub with Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
or following these guidelines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

