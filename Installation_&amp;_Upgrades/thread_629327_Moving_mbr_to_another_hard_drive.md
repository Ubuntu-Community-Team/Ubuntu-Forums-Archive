---
title: "Moving mbr to another hard drive?"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by Bo Mellberg on 2007-12-02
Hello everyone!

I have 7.10 installed on an old IBM xSeries 220 server. The OS is installed on a 73 GB SCSI disk, which ennumerates as harddrive1 in bios. I also have an old IDE drive for music which is harddrive0.

In the bios settings I have selected the boot order to be:

1. harddrive1
2. Floppy
3. CDROM
4. NETWORK

This is all great, until I installed a SATA card with a 250 GB SATA drive. My SCSI drive is not harddrive1 anymore, so "Boot Partition not found" error comes up. I can't set bios to look for harddrive2, so I guess I have to move the mbr to one of the other drives. So, how do I do this? If I connect the SATA drive I can't boot at all.

Another option would be boot from floppy and not mess with the other drives at all. How do I copy the mbr to floppy?

Links to information is greatly appreciated!

/Bo

---

### Post by Pumalite on 2007-12-02
Just reinstall Grub following this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Bo Mellberg on 2007-12-02
> **Pumalite said:**
> Just reinstall Grub following this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks! I just did it without the Live-CD:

1. I sudo:ed into grub and did a "find /boot/grub/stage1". It answered "(hd1,0)" just as expected.
2. In grub: "root (hd1,0)"
3. In grub: "setup (hd0)", to install grub on the mbr of the first disk that is actually found by my bios.

Done. Took the machine down and inserted the SATA drive again. Boots right up, thanks to UUID's I guess.

/Bo

---

### Post by Pumalite on 2007-12-02
That works fine.

---

