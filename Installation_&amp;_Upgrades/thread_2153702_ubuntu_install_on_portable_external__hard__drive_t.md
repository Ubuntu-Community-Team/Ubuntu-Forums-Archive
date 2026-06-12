---
title: "ubuntu install on portable external  hard  drive through usb"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by htanmsa on 2013-06-12
I recently purchased seagate backup plus 1 tb portable external hard drive.
I am using windows 7.
So i want to install ubuntu on my external portable hard drive and use it as a seperate computer.
So whenever i take my portable external hard drive and connect it to other computer or laptop through usb.
i should be able to load linux and my files should be on that portable hard drive.

Is that possible if yes how should do it .

Basically i want my portable external hard drive as another mini laptop which should be able to work to whatever computer i connect.

---

### Post by sudodus on 2013-06-12
Yes, this is possible. You can even install it to a USB pendrive.

You install Ubuntu to that drive almost as if it were a normal internal drive.

When you arrive at the partitioning window (in the installer), you should select 'Something else' and

- do the partitioning and select where to install manually

- at the bottom on the page, install the bootloader to the external drive (and not the default, which is usually the internal drive). *Edit*: Use only a drive letter (no digit, because you should not install it to a partition, so [FONT=courier new]/dev/sdx[/FONT] (not [FONT=courier new]/dev/sdx1[/FONT])).

- do *not* install any proprietary driver, if you want it portable.

If you want to make this safer, you can disconnect or disable the internal drive(s), while you are installing the system.

An alternative is to have a persistent live system, but I recommend an installed system, because it is more stable, and it can be updated and upgraded just like a system on an internal disk.

---

