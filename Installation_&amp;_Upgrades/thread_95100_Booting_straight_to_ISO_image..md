---
title: "Booting straight to ISO image."
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by Doughsay on 2005-11-25
Is it possible to boot straight to the ISO image of an ubuntu install disk?  I'm asking because I'm attempting to install ubuntu onto my toshiba tablet to dual-boot with XP Tablet Edition, but alas, i have no bootable media whatsoever...

I know I could netboot, and I know I could also install GRUB for NT and boot straight to the netboot image instead of through PXE, as describes in this howto:

[http://www.ubuntuforums.org/archive/index.php/t-28948.html](http://www.ubuntuforums.org/archive/index.php/t-28948.html)

But I also came across this thread about booting the Knoppix livecd straight from ISO, and was wondering if this is possible with the ubuntu install cd.

[http://www.knoppix.net/forum/viewtopic.php?t=11796&postdays=0&postorder=asc&start=0](http://www.knoppix.net/forum/viewtopic.php?t=11796&postdays=0&postorder=asc&start=0)

I'm just trying to evaluate all my options.  Thanks for any comments.

---

### Post by aysiu on 2005-11-26
Have you seen [this](http://ubuntuforums.org/showthread.php?t=28948)?

---

### Post by Doughsay on 2005-11-26
> Have you seen this?"

Yes that's (almost) the same post I linked to in my first post.  I know that that's possible, but I was wondering if I can boot straight to the entire install ISO, not just the boot image and have it download the packages.

---

### Post by rpradeep on 2007-01-11
It is possible to install using the ISO alternate CD.

How ever you need to download the hd-media initrd and linux (vmlinuz) files for this from ubuntu site.

During the installtion the installer will search for the ISO in your hard disk but the partition should be in FAT32 (not NTFS)

---

