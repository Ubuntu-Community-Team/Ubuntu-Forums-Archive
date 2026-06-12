---
title: "Problem after partition resize"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by ema on 2007-09-02
Hello,
On my /dev/hda I had the following configuration:

<grub><NTFS XP - boot partition 50G><FAT32 10G><SWAP 512MB><EXT2 25G>

I used gparted to resize the partitions to:

<grub><NTFS XP - boot partition 25G><FAT32 10G><SWAP 512MB><EXT2 50G>

Basically I compressed NTFS partition, I moved FAT, SWAP and moved + resize EXT2
Now, when I restart the PC Grub works and I'm able to boot Linux.
But when I chose WinXP this comes written:
"A disk read error has occourred.
Press Ctrl-Alt-Del to restart".

Then I used the XP CD to make chkdsk (and that CD found out the windows partition...).
Does anyone know how to fix the NTFS partition in order to being able to start XP too?
Btw, I'm able to read/write on it from Linux....

Thanks in advance,
Ema.

---

### Post by merlinus on 2007-09-02
It may be that in shrinking your windows partition, the bootloader got either deleted or moved to another location.

You can use supergrub to first restore windows to the mbr, and then reinstall grub.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Excellent direction for using it here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

-merlin

---

