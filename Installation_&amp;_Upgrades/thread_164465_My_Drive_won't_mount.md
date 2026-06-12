---
title: "My Drive won't mount"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by codypumper on 2006-04-22
I just installed breezy on my HP PC. My Samsung SD-616F dvd drive will not mount. I've dug through the web trying to find something to make it work, but no success. Can anyone help?

---

### Post by cilynx on 2006-04-22
Look at your 'dmesg'.  Is the drive identified?  Does it show up in the "Places -> Computer" thing in Gnome?  What does it do when you try to mount?

---

### Post by codypumper on 2006-04-22
Yes the computer recognizes it there, but it says:

Unable to mount volume. There is probably no media in the device.

Warning: device /dev/hdd is already handled by /etc/fstab, supplied label is ignored
mount: No medium found
Error: could not execute pmount

When I try to mount it, even with a disc in it.

---

### Post by cilynx on 2006-04-22
Guessing by your error that your DVD is /dev/hdd.

If you 'sudo eject /dev/hdd' does that work?
What about 'sudo mount /dev/hdd /mnt'?

---

### Post by codypumper on 2006-04-23
sudo eject /dev/hdd            works
sudo mount /dev/hdd           mount: no medium (even with a disk in it)
sudo mount /dev/hdd /mnt    does nothing

---

