---
title: "trying to recover a crash"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by ipfreak on 2011-04-15
hi all:

upgrading from 8.04 to 10.0.4 failed badly. now i am trying to recover some files on this neo-dead machine.

it keep asking for root passwd i don't know (i didn't install that machine). now i boot this machine up on an usb drive. are there any ways i can savage some of files under /etc/ and /home directory (on the hard drive)?

any help would be greatly appreciated...

---

### Post by Hedgehog1 on 2011-04-15
If you boot the computer from the 10.04 LiveCD/LiveUSB, you can mount the hard drive (it should show in the places menu) and copy data from to an external hard drive (or a USB stick).

There is no password for root on the 10.04 LiveCD/LiveUSB.

If the disk still fights you, you can run nautilus as root by doing this:

```
gksudo nautilus
```

And then copy your data to an external hard drive or USB stick.


***The Hedge***

:KS

---

### Post by d3v1150m471c on 2011-04-15
You should be able to boot up a live cd and copy the media found on the hdd to an external storage device.

---

