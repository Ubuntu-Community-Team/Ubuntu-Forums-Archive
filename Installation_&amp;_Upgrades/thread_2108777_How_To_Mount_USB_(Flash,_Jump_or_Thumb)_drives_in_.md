---
title: "How To: Mount USB (Flash, Jump or Thumb) drives in LiveCD"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2013-01-25
I want to setup an UbuntuOS on a usb flash (jump, pen, thumb) drive. That drive is 8 gig. It has stuff on it. I want to transfer it over to a 32 gig drive and install the Precise Pangolin ver. 12.04 on it. Then I will re-install my Precise Pangolin from scratch (bare metal). The OS broke over an install of MythTV. Maybe there was corrupt data on an encrypted removal drive, too. I'll never know.

I tried to use GParted in LiveCD, but I cannot copy a partition to a different drive. Or at least what I'm seeing when I try that tells me not to do the copy.

I'm in LiveCD just now. I have to thumb drives, one is 8 gig the other 32. I want to move the contents of the 8 to the 32. I used gParted to look at the sizes. There is 15 gig free on the 32 device and only 7 gig on the 8 gig. 

I cannot mount these devices in LiveCD. I see no help via Google search. I wouldn't be asking, otherwise.

Disk /dev/sdd: 8021 MB, 8021606400 bytes
61 heads, 45 sectors/track, 5707 cylinders, total 15667200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001a815

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048    15667199     7832576    b  W95 FAT32

Disk /dev/sdf: 32.2 GB, 32157728768 bytes
90 heads, 26 sectors/track, 26841 cylinders, total 62808064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            8064    62808063    31400000    7  HPFS/NTFS/exFAT

---

### Post by Mark_in_Hollywood on 2013-01-25
Re-booting into LiveCD fixed this.

---

### Post by Mark_in_Hollywood on 2013-01-25
This is **XUBUNTU**. Or was. Something major broke installing/configging MythTV. I used the repos for the front/backend install. Enough. Something broke.

I posted about 48 hours ago, with UUID's etc., but no responses and that tells me it's time for a clean install.

I have, on the LiveCD Desktop: xubuntu-12.04.1-desktop-i386.iso. I moved it to an 8 gig thumb drive to no avail. On Reboot & select boot from USB, screen had cursor blinking, and blinking, and blinking. Nothing else.

I tried the Starup Disk Creator, but it cannot find the xubuntu-12.04.1-desktop-i386.iso. I tried UNetBootin, too, but it won't write to the thumb drive, or won't recognize the above named .iso.

ALSO, I have about 70 gig on this drive for Windows. I'm going to delete that partition and give it to this clean install of Xubuntu/XFCE.

If you know of an app that will backup all the apps I have, e.g., Audacity, Sound Converter, and help me re-install them that would be great.

ALSO, after deleting and resizing the Win partition, how to I update the GRUB? Will that happen automatically on this clean install?

---

