---
title: "How do I get a hardware-autodetecting, modifiable 7.10 onto an external hard disk?"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by thomanski on 2007-12-11
Hi there,

I'd like to essentially have something like a Ubuntu Live CD running straight from my external USB hard disk and I've seen howtos explaining how to get there. In addition to that however I'd like to free the file system that is usually in a squashfs straight-jacket (appropriate for read-only media such as CDs, but not really for my hard disk) and have that writably available so that I can install updates and configure the whole system to my liking at any time.

I've seen remastering scripts, but they essentially allow pre-configuration after which I'd still end up with a non-writable squashfs. I could also do a straight Ubuntu install onto the external hard disk, but then I'd lose the hardware autodetection and would have trouble running from this disk on different computers.

I thought I'd be clever, mounted the Ubuntu 7.10 squashfs of the normal live cd, copied the contents (exclusively) onto a partition of my hard drive, installed Grub and pointed it to vmlinuz and the /boot/initrd... in the boot folder (which strangely ends in .bak) and tried booting into it, but it freezes after a few seconds.

I've kind of run out of ideas and was hoping perhaps someone here could help.

Thomas

---

### Post by thomanski on 2007-12-13
To partially answer my own question:

[http://wiki.ubuntu.com/LiveUsbPendrivePersistent](http://wiki.ubuntu.com/LiveUsbPendrivePersistent) describes a way of getting Ubuntu onto a USB stick or hard disk and run it in persistent mode. Data would then be stored on a second partition, I suspect as a copy-on-write or so. One thing they point out is that you need to make sure to copy the .disk directory from the CD and it turns out that this was the one thing that I hadn't done.

So, I've kind of got step 1 to work now, which is copying the whole CD contents to a partition (as is), setting up grub to point to the /casper/vmlinux and /casper/initrd.gz and have the whole thing boot up as it would from the CD.

I haven't yet tried to get the persistence to work as described in the Wiki, but I'll give that a go soon. However, I'd still prefer, rather than having a copy-on-write, to simply un"zip" the squashfs, copy the contents to the hard disk and have my changes reflected right there. Any hints would be greatly appreciated.

---

