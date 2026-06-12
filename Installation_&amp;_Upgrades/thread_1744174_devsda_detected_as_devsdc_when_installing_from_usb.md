---
title: "/dev/sda detected as /dev/sdc when installing from usb flash drive"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by omaralqady on 2011-04-30
I used a usb flash drive to install 11.04 (using alternate install), and the drive was detected as /dev/sdc when I was making it a startup disk. After installation, the system would not boot, so I checked the grub boot commands, and it turned my hard drive was also detected as /dev/sdc and it even detected its filesystem as msdos2, so I think the two are connected to the flash drive since it is fat32 and is /dev/sdc. I tried to install again using the desktop install, and it also detects the hard drive as /dev/sdc, which will cause the same problem. What can I do to fix this?

---

### Post by dino99 on 2011-04-30
be sure that grub boot on uuid, not on /dev/sdx, or you can set a label on the stick to identify it without confusion

---

### Post by omaralqady on 2011-04-30
Thank you very much :) This worked perfectly :)

---

