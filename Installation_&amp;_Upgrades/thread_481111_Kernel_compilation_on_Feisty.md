---
title: "Kernel compilation on Feisty"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by MatBi on 2007-06-22
Hi,
i'm recompiling the 2.6.20 kernel from the linux-source package. In [this]("http://ubuntuforums.org/showthread.php?t=56835") howto is recommended to enable initrd as follows:

[FONT="Courier New"]make-kpkg --initrd --append-to-version=-custom kernel_image[/FONT]

As far as i understand, Feisty uses initramfs, and therefore the option "--initrd" is not needed anymore.
Can anyone confirm this?

Furthermore, when i install the deb package, it cannot find some files under /lib/firmware. I symlinked the older kernel directory, but i'm not sure it's the right solution. 
Hints or comments?

Thanks in advance,
MatBi

---

