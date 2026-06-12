---
title: "Grub not working anymore - error: unknown filesystem"
date: 2020-03-13
forum: Installation &amp; Upgrades
---

### Post by bobalazek124 on 2020-03-13
Hello!

I'm experiencing an issue - up until today I had installed windows & ubuntu in dual boot. Because I wasn't using ubuntu at all I decided to remove the volume via windows' device manager and make into a ntfs partition for windows. All good until I restarted the PC. Then I got:
error: no such device: d566c245-....
error: unknown filesystem
Entering rescue mode

Luckily I had boot repair on an usb, but that didn't solve anything & I ran it twice.

Then I tried to manually set stuff via the grub rescue terminal:
set root=(hd0,msdos2)
set prefix=(hd0,msdos2)/boot/grub
insmod normal
// here I just get - error: unknown filesystem
Also tried the same with (hd3,msdos1), but same issue

What am I doing wrong? For windows - I have the newest windows 10 installed if that helps.

Here's the pastebin:
[http://paste.ubuntu.com/p/9c7DvSvGfd/](http://paste.ubuntu.com/p/9c7DvSvGfd/)

---

### Post by bobalazek124 on 2020-03-13
Actually - I think I just found the issue. In my UEFI boot I just needed to set my primary SSD, where windows is installed, to the first priority. Strange that it was working until now with grub with the wrong order. Anyway, can be closed!

---

### Post by yancek on 2020-03-13
Your Grub menu after you installed Ubuntu would have had an entry to boot windows.  Grub code in the EFI partition points to the Ubuntu partition where the actual Grub menu exists.  Since you deleted/formatted the partition on which Ubuntu was installed with the Grub menu needed, that is the reason you got the error "no such device:, that ext4 Linux filesystem UUID no longer exists and the second line "unknown filesystem" is because it is looking for an ext4 filesystem and you formatted it ntfs.

> error: no such device: d566c245-....
error: unknown filesystem

---

