---
title: "Error: Unknown filesystem"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by DarkBowser on 2012-07-14
I had Ubuntu 12.04 lts on a 320GB HDD. I got an new HDD, and formatted the old 320 for extra space. I now installed windows on the 320. But when I boot it says Error?: Unknown filesystem. Grub rescue.

How the F**K do I get rid of this? I already tried the windows rescue cd and that didnt work. HELP

---

### Post by darkod on 2012-07-14
So, do you also have a new ubuntu installation? In that case you probably have the new grub2 on the new disk. On the old disk the grub2 remained and is now broken since the old ubuntu partition is deleted, because formatting doesn't remove the bootloader.

Be careful with the windows rescue commands, it can overwrite your good grub2 on the other disk because it never tells you where it will put the windows bootloader.

In fact, that's what you might have now, windows bootloader on the new disk (which can't boot ubuntu) and broken grub2 on the old disk from the old install.

First try going into BIOS and set the new disk as first option to boot from.

In case that just boots windows directly, you will need to use the ubuntu cd in live mode and put grub2 back. If you need help with that, ask and post the results of:
sudo parted -l

from live mode.

---

