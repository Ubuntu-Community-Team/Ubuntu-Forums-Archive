---
title: "Missing SWAP partition after clean installation"
date: 2016-01-08
forum: Installation &amp; Upgrades
---

### Post by hugodaniel2 on 2016-01-08
Hi,

I just installed Ubuntu 14.04 LTS on a Desktop computer with a 150 GB HDD, but after the installation was finished (it froze at the end, and I needed to reboot the machine) I discovered that somehow the LVM partition that was created didn't include a SWAP partition.

I've tried to use GParted to resize it, so that I could free up some space to create that partition manually, but its locked, I can't do anything, even using the Live CD "Boot-repair-disk", which also has GParted. 

[ATTACH=CONFIG]266609[/ATTACH]

During the boot process it give an error message, saying that the system can't mount any SWAP partition, and of course, it won't, because there is any, but I can't understand why it didn't created one from the beginning.
Have I've done something wrong?

Is there any way to resize the partition, and to create the partition manually, without having to format the drive again?

Thanks!

---

### Post by Dennis N on 2016-01-08
You need to unmount both the sda5 and sda2 partitions before you can resize sda5. 
Also, your boot partition is small. Keep close watch on that, as it will fill up quickly.

---

