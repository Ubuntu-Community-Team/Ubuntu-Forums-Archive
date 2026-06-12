---
title: "Booting an already installed ubuntu from usb external drive"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by diegovar on 2010-04-05
Hi, I'ts my first post here, a long time Ubuntu user :)

I've installed Ubuntu 9.10 in an internal SATA drive and used it for quite a while, but yesterday my laptop's graphics card decided to die, and it looks like it will be a full month until I get replacement m/b. Therefore, I bought an external USB SATA Hub for my laptop's drive, but I can't seem to be able to boot ubuntu from this drive. I'm trying to boot with this external usb hub attached to an old P4 machine with USB booting enabled.

I get till the grub screen, but as soon as the message "Grub loading" appears, I get a message saying:

error: no such partition

and I get a prompt as follows:
grub-rescue>

I guess grub is trying to boot to a different device name... It's weird, I thought Ubuntu should boot irregardless of which interface I use, be it SATA or USB...


Any help regarding this issue?

Thanks

Diego

---

### Post by Tylerjd on 2010-04-05
Well, I would boot a live cd, go to terminal, and do ```
sudo grub-update /dev/sdb
```*sdb could be different depending on the system.

---

### Post by diegovar on 2010-04-05
grub-update doesn-t seem to exist in Grub2.

Running sudo update-grub yields:

```
grub-probe: error: cannot find a device for /.
```


if I run sudo grub-install /dev/sdb, I get:

```
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```


Any ideas?

---

