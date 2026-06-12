---
title: "Installing on a laptop w/o cdrom support and partition resize issues"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by Dlrnc3 on 2007-04-18
I've played around with a few different types of linux on my desktop before, but never ubuntu. I would like to install it on my laptop but I've been having difficulties finding a free partition resizer that actually works. I have a PCMCIA cd-rom but even though cdrom is first on my bios boot order, it skips the ubuntu disk and boots xp without any messeges. I read about installing right from the image without any cd's necessary but thats a little too complicated since I dont want to risk damaging my windows installation too much. If anyone has any recomemdations please tell me. I have an Acer Travelmate C110.

---

### Post by ALIENDUDE5300 on 2007-04-19
I use GParted to resize my partitions. You can try that too if you want.

---

### Post by Dlrnc3 on 2007-04-19
It looks like that is just for linux. I need something that will resize my disks before I install ubuntu so I don't ruin my windows installation.

---

### Post by krugger on 2007-04-19
Try looking up PXE install. You will need another computer to offer you a boot image. This will be just like installing from CD. I use it for some old laptops which don't have cdrom or floppy. Resizing partitions that are in use is a very tricky business and I wouldn't recommend it.

---

### Post by Dlrnc3 on 2007-04-19
So then there is no good way to go about resizing my partition? I could just put ubuntu on an external but I would rather it on the actual disk. I'll look up this PXE install though, thanks.

---

### Post by ALIENDUDE5300 on 2007-04-25
> **Dlrnc3 said:**
> So then there is no good way to go about resizing my partition? I could just put ubuntu on an external but I would rather it on the actual disk. I'll look up this PXE install though, thanks.

I already mentioned GParted. It is technically just for linux but I used it to resize my NTFS partition before installing ubuntu. You can get the live cd and boot from that. here are some helpful links:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

And here are screen shots for the livecd:

[http://shots.osdir.com/slideshows/slideshow.php?release=774&slide=1](http://shots.osdir.com/slideshows/slideshow.php?release=774&slide=1)

Sorry about the slow response -- I hope I could help!

---

