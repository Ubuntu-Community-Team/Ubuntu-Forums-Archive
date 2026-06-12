---
title: "Changing from HDD to FlashDrive"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by Turbofly on 2011-01-22
Does anyone know if it would be possible to copy/clone my current Ubuntu install to a memory card of usb stick, and then boot from it? I have a HTPC and the hard drive is the loudest component in the pc. I was hoping that running it from a flash drive would be a lot quieter.

---

### Post by oldfred on 2011-01-22
I am pretty sure there would be a way to copy it, but I prefer clean installs. Then copy /home and export & add installed programs.

The flash drive will be slower than a hard drive since writes are slow and USB port is slower than hard drive. It should be functional.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by C.S.Cameron on 2011-01-22
you should be able to shrink your hard drive partition to a size that will fit your USB stick and then copy over, all using gparted.
You will need to add grub to your flash drive after.

As Fred says it will be slower than running off the hard drive.

---

