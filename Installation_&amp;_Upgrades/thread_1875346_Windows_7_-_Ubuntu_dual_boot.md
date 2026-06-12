---
title: "Windows 7 - Ubuntu dual boot"
date: 2011-11-04
forum: Installation &amp; Upgrades
---

### Post by manoyth on 2011-11-04
I have a laptop with windows xp and windows 7 installed (dual boot). I want to delete windows xp and install ubuntu without deleting windows 7. Does anyone know how to do it?

---

### Post by zvacet on 2011-11-04
You can do it during Ubuntu installation.When you get to the partitioning step ( or where to install Ubuntu) select other (I think that is correct because I don´t use English version) and you will have choice to delete partition.Be careful and delete right one and that unallocated space format as ext4 and give partition mountpoint /root.When you finish installation Ubuntu boot loader will recognize Windows 7.

---

### Post by darkod on 2011-11-04
There is only one thing to consider before deleting the XP partition. Windows is designed so that it combines the boot files if you have 2 or more version of windows installed.
If XP was installed first, most probably the win7 boot files are also on the XP partition.
You can easily check if you select in windows to show you the hidden files and protected system files.
Then look for the bootmgr file (the win7 boot file). Is it on the XP partition or on the win7 partition?

---

### Post by manoyth on 2011-11-05
Bootmgr file is on the xp partition

---

### Post by darkod on 2011-11-05
Then you can't simply delete it. You can, but your 7 will not boot any more. Although the repair process of win7 boot is simple using the win7 dvd.

Probably the best is:

1. First investigate how to restore the win7 boot files. Google for "how to restore win7 boot files" or similar. If the process looks simple to you, go forward.
2. Boot with the ubuntu cd in live mode, open Gparted and delete the XP partition. Make sure you delete the correct one. DO NOT install ubuntu yet.
3. Reboot with the win7 dvd and repair the boot process. Make sure you can boot win7 OK.
4. Now boot with the ubuntu cd again and start the install. Either create your partitions manually from the unallocated space left with the XP deletion, or just tell the installer to use the largest available free space and it will install automatically in the unallocated space.

That should be it.

---

