---
title: "[SOLVED] Dual-boot Windows reinstallation broke grub"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by Neuge on 2007-09-04
I have a Dell laptop that I dual-boot with XP and Feisty.  I recently reinstalled Windows because it was getting a bit sluggish and, of course, it rewrites the MBR.  So I fired up the Live CD and tried to rescue grub by:

sudo grub
find /boot/grub/stage1
root (hd0,6)
setup (hd0)
quit

That restored the grub menu on boot, but when I select Ubuntu it returns "Error 15: File not found".  I can boot to XP fine, but selecting either Ubuntu kernel, their respective recovery mode, or memtest returns that error.  I've tried going through both the live CD and alternate CD installs to manually set the / and /home mount points without installing the base system, but it won't let me.

Any help would be appreciated, I'd rather not reinstall completely.

EDIT:  Oh, this is 64bit, if that matters.

---

### Post by kagashe on 2007-09-04
[Gentoo Grub Error Collection]("http://www.gentoo.org/doc/en/grub-error-guide.xml?style=printable")

Nice documentation for all Grub errors.

kagashe

---

### Post by forestpixie on 2007-09-04
this might help - the ubuntu grub recovery [page]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Neuge on 2007-09-04
Figured it out guys, thanks for the help.  For some reason every time  I recovered/reinstalled grub it set the file system mount point in /boot/grub/menu.lst as (hd0,7) when it should've been (hd0,6).

I just went in and manually edited menu.lst to make it right.

---

