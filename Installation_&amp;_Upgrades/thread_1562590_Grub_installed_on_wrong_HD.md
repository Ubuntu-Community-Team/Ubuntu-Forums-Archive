---
title: "Grub installed on wrong HD?"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by UnixHackerBeard on 2010-08-27
Hi all, I have two HDs and recently reinstalled Ubuntu. However, I think grub may have installed to my media drive and not my main HD.

Here is the output of fdisk -l:
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000dfd9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37573   301805091    b  W95 FAT32
/dev/sda2           37574       38913    10763550   83  Linux

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b873d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29652   238171136   83  Linux
/dev/sdb2           29652       30402     6025217    5  Extended
/dev/sdb5           29652       30402     6025216   82  Linux swap / Solaris

```/

dev/sda1 is my media drive and I think during setup grub-install may have been automatically run on /dev/sda1. If this is the case, 

1) How can I remove grub from sda1 and install it on sdb?
2) Should it be on sdb1 or sdb2?
3) Can I change the naming so my main drive is sda and my media drive is sdb?

---

### Post by presence1960 on 2010-08-27
That info doesn't show where GRUB is installed. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

