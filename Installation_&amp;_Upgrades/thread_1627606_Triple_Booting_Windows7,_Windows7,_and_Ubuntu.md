---
title: "Triple Booting Windows7, Windows7, and Ubuntu"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by irwineffect on 2010-11-21
My system set-up is one HDD that is partitioned having two Windows7 bootable partitions, and Ubuntu. I originally had Windows7 and Ubuntu, but I wanted to have another Windows7 OS to keep clean for gaming. Of course, when installing Windows7 it wiped out Grub2. I've reinstalled Grub2, but now I'm having a problem in that when I choose Windows7 in the Grub menu, it directs me to the windows boot manager to choose one of my Windows7 partitions to boot. I'd like to configure Grub so I can choose which Windows7 installation I'd like to boot from there. I've tried added custom scripts to point grub directly at the partition where each installation is located, but it always directs me to the windows boot manager. How can I bypass that?

---

### Post by Hippytaff on 2010-11-21
did you do
```

sudo update-grub

```
also have a read of this
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)
:-)

---

### Post by oldfred on 2010-11-21
Grub cannot boot the second windows as windows installs the second copy & then moves the boot files to the first copy of windows. Your second copy has no bootable files.

You did install the second copy to a primary partition? If so you may be able to move boot flag and repair it.

Otherwise you can reinstall.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

