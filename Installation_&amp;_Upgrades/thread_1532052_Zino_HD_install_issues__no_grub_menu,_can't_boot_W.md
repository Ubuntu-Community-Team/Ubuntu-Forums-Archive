---
title: "Zino HD install issues : no grub menu, can't boot Windows"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Zercius on 2010-07-15
Hey folks. I just got a Zino HD from Dell, and was planning to use it connected to my TV, dual booting Xubuntu 10.04 and Windows 7.  I did, however, run into some issues. I suspect I'm just going to have to burn a restore disc and start over, but I'd like to fix this if possible. Here's what I had to start with:

1 vfat partition (bootup?)
1 dell restore partition
1 Windows partition

Because the restore partition was a bloody 20 GB, and I could always get the restore done via disc, I reformatted it as ext4 and used it as "/". I then shrunk the Windows partition and allocated a home partition and some swap space. Note that immediately after the installer, I reformatted the home partition manually with an inode size of 128 to use with the Windows ext2 driver, but that shouldn't have really changed anything.

End result file system order:
1 vfat
1 ext4 mounted as "/"
1 Windows
1 Swap
1 ext3 mounted as "/home"

I now have two problems:
1) I do not get any GRUB menu at all! It just boots directly into Xubuntu with no choices (not even memory test or restore mode).
2) I, obviously, can no longer boot Windows.

Any suggestions? Keep in mind that this a fresh install on a brand new machine; I can't think of any reason GRUB wouldn't even show me a menu.

---

### Post by Zercius on 2010-07-17
Okay, I'm going to mark this as Solved, since I figured out what has gone wrong, although I have not (yet) fixed it. Turns out the restore partition was ALSO the Windows 7 partition, so erasing it rendered Windows 7 unbootable. GRUB thus did not recognise Windows 7 as a boot option, and since the only other options were for debugging, it apparently didn't bother to show me a boot menu. Dell will be sending me a restore disc (stupid download service requires me to use the machine itself to authenticate), and I will restore Windows 7 when that comes.

---

