---
title: "failed initramfs after upgrade and power outage"
date: 2010-08-06
forum: Installation &amp; Upgrades
---

### Post by carpman on 2010-08-06
Hello, did an update from ubuntu 8 to 10.04, this has failed.

At boot there is initramfs error with prior message saying.

```
alert /dev/disk/by-uuid/-the_uuid does not exist dropping to shell
(initramfs)
```

I boot to livecd and check disk uuid and compared it to the fstab and it is correct, is there anywhere else this uuid but have been corrupted or any issue that may cause this issue.


note there was power cut during upgrade but this occurred when upgrade should have finished.

fschk was run and is clean.


cheers

---

### Post by lechien73 on 2010-08-06
A solution to this was posted here: [http://uri.tl/v](http://uri.tl/v)

Although, I would have thought that booting from Live CD and re-installing Grub might help, since it could be that Grub is unable to find the second stage file on your hard drive, for some reason.

---

