---
title: "Installing ubuntu 10.10 onto a flash drive"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by hatewindows on 2010-10-15
I want to install ubuntu onto a flash drive and be able to use it on any PC--booting from the USB drive.. I currently have 10.10 installed on machine now-so do i still have to download the ISO file? Thanks...

---

### Post by oldfred on 2010-10-15
I do not think there is any easy way to copy from a hard drive to a USB flash drive.

maverick screens are a little different but the process is the same.
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1 
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

See C.S.Cameron Posts ( But I do not unplug hard drive, just use advanced button to install grub to USB's MBR) 
[http://ubuntuforums.org/showthread.php?t=1509603](http://ubuntuforums.org/showthread.php?t=1509603)
[http://ubuntuforums.org/showthread.php?t=1539342](http://ubuntuforums.org/showthread.php?t=1539342)

---

### Post by C.S.Cameron on 2010-10-15
> See C.S.Cameron Posts ( But I do not unplug hard drive, just use advanced button to install grub to USB's MBR) 

Thanks Fred.
Minor detail but 10.10 does not have an advanced tab after partitioning.
If you choose manual partitioning there is a spot where you can choose the location for grub. (However I still prefer unplugging the hard drive myself, as it makes a neater grub.cfg file).

---

### Post by oldfred on 2010-10-15
C.S.Cameron, I forgot the change in Maverick. If not manually partitioning, your way may be the only way.

I also understand that the combo box to install grub only is shown if you use manual install. I always manually partition in advance so I did not know that until someone mentioned it recently.

---

