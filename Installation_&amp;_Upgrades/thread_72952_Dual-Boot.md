---
title: "Dual-Boot"
date: 2005-10-07
forum: Installation &amp; Upgrades
---

### Post by Christopher999999 on 2005-10-07
I want to dual a dual boot with Windows 98 SE and Ubuntu. Can somebody help me?

---

### Post by Emerzen on 2005-10-07
Here is a gross outline:

1.) Defragment Windows.
2.) Shrink Windows partition: you can run qtparted from Knoppix for this (free) or buy a copy of Partition Magic.  **This step is only necessary if you don't have any free space on your harddrive**
3.) Install Ubuntu into the new freespace.  Have GRUB installed over MBR (and it should automatically detect Windows and give you Windows option in main boot Window).

Let me know if you need more specifics w/ this.  If you could post some system spec's that'ld help...particularly your hard drive(s).  I'm assuming you've tried the Live CD and everything work's okay?

---

### Post by dhracer1067 on 2005-10-07
Hey. This is my first time installing and I was wandering what file format i had to have my partition on to install it.

---

### Post by SilentCacophony on 2005-10-07
[QUOTE=dhracer1067]Hey. This is my first time installing and I was wandering what file format i had to have my partition on to install it.[/QUOTE]

Hi. You can choose from several, with ext2, ext3, and rieserfs being common. I personally prefer ext3 or rieserfs for the journalling, which reduces data loss possibility.

---

### Post by Herman on 2005-10-07
Hello Christopher 999999 and dhracer,
                                                   In adition to the information others have posted above, I have a couple of good links here to make things easier for new dual-booters. The first one is by zcox, and is excellent for those who have either a FAT32 or an NTFS file system in Windows.

[http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html](http://ca.geocities.com/zachandloricox@rogers.com/ubuntu/ubuntu.html)

The second link is my signature link, (below), which is more relevant to those who have a FAT32 file system in Windows. I recommend zcox's link for those who have NTFS.

You should be okay if you check them both out. Enjoy! ;)

---

