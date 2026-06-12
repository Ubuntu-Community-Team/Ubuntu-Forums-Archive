---
title: "GRUB Not Finding HDD!"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2013-01-25
Oh dear God, help me! I tried to reinstall Ubuntu over an old partition that had ubuntu previously, but wouldn't boot due to graphics driver issues, but when I try to boot my laptop, it says this:
[http://i.imgur.com/mDCC4yi.jpg](http://i.imgur.com/mDCC4yi.jpg)

---

### Post by darkod on 2013-01-25
It didn't install the grub2 bootloader it seems. It still has the old one on the MBR but the old partition is gone now.

Simply reinstall grub2 to the MBR of the boot disk using the ubuntu cd. You have instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by oldos2er on 2013-01-25
See [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by amtur_poet on 2013-01-25
> **oldos2er said:**
> See [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Thank you; that did the trick. :)

---

### Post by oldos2er on 2013-01-26
Great! Would you please mark the thread as 'Solved' under Thread Tools? Thanks.

---

