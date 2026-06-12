---
title: "Creating a Bootable USB Stick Fails on 14.04"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by actionmystique on 2014-04-23
I'm still trying to create a bootable USB stick with "**Startup Disk Creator**" and it does not work: **it says there is not enough  space, whereas the stick is empty**:

[ATTACH=CONFIG]252416[/ATTACH] [ATTACH=CONFIG]252417[/ATTACH]

---

### Post by sudodus on 2014-04-23
I would (install if necessary and) try ***gparted*** to create a partition on the USB pendrive, and format it with the ***FAT32*** file system (instead of an ext file system) and try "**Startup Disk Creator**"again.

---

### Post by actionmystique on 2014-04-24
Thanks, straight to the point; you've found the glitch! It's rather surprising that we cannot boot with an ext4 USB stick, but at least, I was able to create a GPT table on it.

---

### Post by sudodus on 2014-04-24
You can boot with an ext4 USB stick, but then you need another tool/method to make it bootable. For example, you can make a 'normal installation' into a USB drive, and then have a portable linux 'installed' system. Such a such will normally have a root partition with the ext4 file system.

---

