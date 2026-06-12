---
title: "Portable 'installed' system swap"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by sudodus on 2013-04-04
I have a USB 3 boot pendrive, where I  have installed Lubuntu 12.04 + Xubuntu desktop. I have no proprietory  drivers in the system, so it is ***generally portable***, runs with Intel, Nvidia and Radeon graphics. I'm quite happy because this way I can easily borrow a computer and run my own system with my own settings, bookmarks, passwords, and some personal data files too.

I wanted to have ***encrypted home***, and it works well. But it implies encrypted swap, and ***the system started hijacking the swap partitions from the installed systems***. This happended if there was a linux swap partition available, even when I made a small swap partition on the USB drive and let the system encrypt it. This 'wanted' cryptswap had a line in /etc/fstab pointing to it, but the system wanted more. It is described in a manual page, that cryptswap tries to encrypt the swap it finds for security. *But I don't want it in this case*.

I tried a lot of things, including to remove the software, that is used to create cryptswap **[SIZE=3][FONT=courier new]/sbin/cryptsetup[/FONT][/SIZE]** but then the existing cryptswap could not be used. Finally I made a regular swap partition, made an entry in /etc/fstab and kept that software removed (actually moved to another directory outside PATH). Then it couldn't hijack swap, and the encrypted home is still working well.

This is security hole. But I work around it with a script that wipes the swap if it is used (usually I don't need swapping). If swapping was needed, and I want to remove any traces, it will overwrite the swap partition and make a fresh one at the same place and with the same UUID. It takes about one minute for 2 GB, which is definitely OK for me.

I know discard is nicer for the hardware than dd, and it should work with a swapfile on an SSD. But I don't think discard works on a USB pendrive. I'm sure there are better solutions for this problem, maybe it is simple, maybe not.

Please help me!

---

### Post by roten on 2013-04-04
I suggest you use another system or method if security is important. Otherwise maybe it's OK without encrypted home.

- tails, special security operating system (debian)

- encrypt the whole usb drive

- or what you half suggested yourself: use an external SSD drive with a swapfile and use discard to wipe it. Use hdparm to test that discard works. It can be connected via usb3 and esata. Bigger, yes, but still much smaller than a netbook or ipad.

---

### Post by sudodus on 2013-04-04
Thanks for the tips :-) I will look into the details.

> **roten said:**
> I suggest you use another system or method if security is important. Otherwise maybe it's OK without encrypted home...

Do you mean without encrypted swap (like it is now)?

---

### Post by C.S.Cameron on 2013-04-04
Why do you want swap on a flash drive?
I'm not sure I have ever seen a real benifit.

---

### Post by sudodus on 2013-04-05
> **C.S.Cameron said:**
> Why do you want swap on a flash drive?
I'm not sure I have ever seen a real benifit.

I'm glad you found this thread :-)

Not because I'm intending to use swap, but because at some rare instances, writing to swap might keep an application or the system working, and with a USB 3 pendrive it is fairly fast (even in a USB 2 port because the flash is faster than standard flash for pendrives). Remember I want this to be a truly portable system. So I don't want it to mess with any file on an internal drive, unless I decide to mount it and use it.

I haven't tried (yet) what happens if I remove all references to swap in the /etc/fstab file, maybe it stops hijacking swap files/partitions on internal drives.

---

