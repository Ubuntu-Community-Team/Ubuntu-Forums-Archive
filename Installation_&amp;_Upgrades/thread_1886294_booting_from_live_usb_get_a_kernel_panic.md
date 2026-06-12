---
title: "booting from live usb get a kernel panic"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by Oxyris on 2011-11-24
I don't know what happened. I created a usb with ubuntu 11.10 and I was successfully able to boot into it twice on my laptop. Then I tried to boot into a desktop and I got a kernal panic "Linux Kernel panic: VFS: Unable to mount root fs" so I tried with my laptop and the same thing happened. I can't imagine how the usb got corrupted in the span of a day but I guess it happened. So what are my options? Can I fix this or should I re-create the live usb?

---

### Post by Schugy on 2011-11-25
Maybe you have altered the drive setup. Adding/removing another USB-stick or putting a SD card into the card reader may change a drive sdc to sdd e.g.. Add something like root=UUID=88d9b5d2-d654-27fe-b863-ac3b0125a7cb to the append line at the isolinux boot menu.
fdisk -l should show a working partiton table.
Use fsck.vfat or fsck.ext2 to recover from filesystem errors.

---

