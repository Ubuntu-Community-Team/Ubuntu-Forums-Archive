---
title: "Strange Occurances After 6.10 Install"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by terces on 2006-11-21
Among a few reasons I decided to ditch 6.06 and do a fresh install of 6.10.  I keep my /home on a separate hard disk.

Everything installed successfully though since I have three hard drives (some in RAID) in the tower I wasn't sure what was hd0 and hd1 so I took a guess and installed the grub bootloader to hd1.  Turns out it should have been hd0.  So I fired up the cd, mounted the root partition, and edited the menu.lst so that grub would successfully load Ubuntu.

Now, I've noticed some strange things.  For example, if I have a launcher in the top panel and I move it within the launcher, the icon turns to the ? sign with no run info.  Another thing is that there is an inch gap between the desktop views and the trash can in the lower right of the screen.  Another is the volume icon - it too is about an inch from the date and time.

Any ideas why things are kinda funky?  I did check the CD's integrity before installing and all checksums were OK.

---

