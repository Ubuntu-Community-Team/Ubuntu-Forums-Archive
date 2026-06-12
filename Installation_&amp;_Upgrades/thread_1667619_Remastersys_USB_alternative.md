---
title: "Remastersys USB alternative?"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by ivarn on 2011-01-15
Hey. I wanna make a LiveUSB backup with installation usb. The problem with remastersys is the 4gb limit. I have a 32gb usb stick so that is why I wanna do it this way instead.
SO, is this possible, or is CD with remastersys the only solution?

---

### Post by C.S.Cameron on 2011-01-15
Is not 4GB the limit for FAT32 file size?

You can clone your your Bootable USB with dd:

```
sudo dd if=/dev/sda of=/dev/sdb
```


Where sda is the drive you wish to clone and sdb is the target drive.

Very powerful be cautious.

---

