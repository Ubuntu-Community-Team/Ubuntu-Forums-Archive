---
title: "screwed with my mbr and I thought it wasn't supposed to"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by xwingband on 2007-05-04
Now it's been a while since I futzed with Ubuntu.  I stopped at Dapper Drake.

What I did then when I installed was I told the install to use a USB thumb drive as my boot partition.  Then the main mount was on an external hardrive...

I thought I did the same when I went into my new Feisty Fawn installation.  Apparently not... I still can't boot without the thumbdrive but it put grub on my normal internal drive.

This has ticked me off because I don't want grub popping up when I'm booting normally.  I specifically set it up like that before so it didn't touch my Windows drive and booted like normal if I didn't tell the BIOS to boot from the USB.

So my question would be... aside from figuring it out and stomping the install what can I do to get this the way I like?  I've fixed the mbr before, so that's not an issue.  I'm just unsure if I can move grub around.

---

### Post by psusi on 2007-05-04
Run fixmbr from the windows recovery console to fix your internal disk, then you need to install grub to the external disk.  Boot from the livecd and assuming the external disk shows up as /dev/sdb, and the partition you installed ubuntu to is /dev/sdb1, do this:

sudo grub
device (hd0) /dev/sdb
root (hd0,0)
setup (hd0)
exit

Now you should be able to tell your bios to boot from the usb disk first, and ubuntu will load if the disk is plugged in.  Unplug it and you should boot windows from the internal drive.

---

### Post by xwingband on 2007-05-04
Awesome, that seems easy enough.  Thanks for the help!

---

