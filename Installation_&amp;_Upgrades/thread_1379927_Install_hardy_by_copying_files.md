---
title: "Install hardy by copying files"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by amsterdamharu on 2010-01-13
I have Ubuntu Hardy (8.04) on my desktop and want to put it on my laptop, currently my laptop has Fedora and win xp. 

I was thinking not to go through a lengthy setup and just copy the ubuntu files from my desktop to my laptop (untar a backup made with a tiny core boot usb). 

My guess is that I have to delete the xorg.conf and re setup my videocard. But is there any other hardware that ubuntu won't initialize on startup?

Thanks for reading.

---

### Post by barnex on 2010-01-13
I guess your bootloader won't work, so unless you know how to clone disk images, I would just suggest to do the clean 'lengthy' setup anyway. It will probably be faster than trying to clone your system and then having to fix many issues afterwards.

---

### Post by amsterdamharu on 2010-01-13
System already has grub (fedora) thinking of just restoring an Ubuntu backup to the partitions that are currently in use for fedora. If it doesn't work I will do a lenghty install.

---

### Post by barnex on 2010-01-13
Well, I guess that can't hurt. Let me know if it worked!

---

### Post by wkulecz on 2010-01-13
Should work fine, unless you've installed a hardware specific kernel instead of the "generic" one.  

I do this a lot to "clone" systems using rsync.  Keep a live CD handy to reinstall grub and edit /etc/fstab to fix the UUID disk mount errors or the mysterious /dev/hda vs. /dev/sda IDE drive assignments I see on some systems.  If both systems will be on-line at the same subnet you'll have to change the hostname of one of them.  Not as issue for me as the clones are shipped off other locations.

--wally.

---

### Post by amsterdamharu on 2010-01-22
It worked, no need to change the fstab or xorg.conf, just booted in recovery and choose fix x. The Intel Mobile 945gme does not have 3d effects (as it had in fedora) but that can be fixed.

Needed to change the menu.lst since this uses uuid for root drive that is invalid.

Thanks all for your help

---

