---
title: "Installed Ubuntu, then Xp, can't boot into Ubuntu"
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by Demagogue51 on 2006-07-15
Title explains it all.  On my hard drive I have my 10 gig ubuntu install, then the 512mb swap, then the 65 gig ntfs partition.  Any help would be greatly appreciated.

---

### Post by ... on 2006-07-15
What happened is that XP put it's bootloader over GRUB.  The easiest fix is to install ubuntu again (if you put any effort into the install, use a livecd that has ntfs support to copy all of the files from the ubuntu partition over to the ntfs one, then reformat the ubuntu one, install ubuntu, then use the live cd to put them back; just replace all of the files the installer made). Then you have grub back, and you can boot XP from there.

If you are feeling adventerous you can look at the grub site (google it) and install if yourself...

Good luck!

---

### Post by aysiu on 2006-07-15
Take a look at the first or second post of this thread:
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

