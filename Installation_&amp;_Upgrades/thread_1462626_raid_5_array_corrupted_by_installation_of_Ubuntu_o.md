---
title: "raid 5 array corrupted by installation of Ubuntu on non-raid disk"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by nrasmith on 2010-04-25
Hello all,

After setting up dual-boots of windows 7 and Ubuntu (9.10 and 10.04) on a number of different desktop PCs and Notebooks/Netbooks without encountering any problems, I have decided to install Ubuntu onto a dedicated HD on my main desktop PC.

On this PC, I have been running a hardware raid5 (3 x 320 GB) array with the Windows 7 64-bit OS.  Previously I used this array for everything (work, games, music, etc.), but now I want to use Ubuntu for everything apart from games - for which I wish to keep my Windows 7 raid5 array.

I have successfully installed Ubuntu 10.04 onto a seperate HD, and I have the ability to boot into both windows 7 (raid5) and Ubuntu 10.04 (non-raid).  The only problem is that the Windows 7 raid5 array has become corrupted, by this I mean that the startup raid screen upon booting the PC tells me that the raid5 array is in rebuild status, and some applications in windows 7 have become corrupt.

The only thing that I can think of that may have caused this issue is the Ubuntu volume somehow writing data onto the raid5 array, or partitioning a small chunk of it - possibly for the the bootloader (GRUB) to reside on.

Can anyone help me sort out this problem?  If it is indeed caused by GRUB, can I "re-install" it onto my non-raid Ubuntu HD?
Also, if i simply rebuild my raid5 array, will this sort out the problem?

Thanks in advance...


Nick

---

### Post by nrasmith on 2010-04-30
Well, I've been procrastonating about rebuilding the raid 5 array all this week.  I booted into windows last night only to find a black background and no desktop icons, i guess explorer has stopped working properly.

The best way that I can use to rebuild the array is to use intel storage manager software.

Since windows has become corrupt, and applications will not run correctly, can I rebuild the array through ubuntu, using the intel matrix storage manager software?

---

