---
title: "LiveCD with persistent - unclear unmount."
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by iX9 on 2017-06-09
Hi! :p
I use Kubuntu 14.04 LiveCD on USB with **casper-rw** persistence.
All is OK, but after I use this and reboot to windows, it says "USB drive need to check", but found no errors.
Probably unclear unmount from casper-rw??
Is there some way to fix it? Add somewhere to LiveCD shuting-down script or command that forces clear unmount of casper-rw before reboot?
THNX!

---

### Post by yancek on 2017-06-09
Do you have a casper-rw file or a casper-rw partition?  A casper-rw partition needs to be a Linux filesystem which windows doesn't understand so that may be the reason for the error.  I'm not sure why you would leave the usb attached when booting to windows.  You can't modify the live OS as it is read-only so the only thing you could do is write to the casper-rw file.  If it is a casper-rw partition with a Linux filesystem, a default windows will not recognize it and won't be able to read or write to it.

---

### Post by iX9 on 2017-06-12
I have casper-rw on the same USB like LiveCD (YUMI install).
Its VFAT (FAT32) writtable. Casper-rw itself is EXT4.
Unclear unmount is the FAT32 filesystem.
I use this stick for multiboot, so I use it in windows too.
Is there a way, how to force unmount casper-rw before I shutdown the LiveCD?

---

