---
title: "Grub won't install on right drive, not going onto (hd1)"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by LeotCol on 2010-02-04
I'm trying to install ubuntu on a portable 30 gig hard drive. My BIOS does support USB booting. I've tried installing it a few times now. I clean the drive out so its all unallocated space. Then I boot from the disk and choose the second hard drive in the advanced tab.

I tried everything. It says sda for my internal drive and sdb for my external. When I choose sdb it is definitely not on the internal drive...but it won't boot.

This is the latest ubuntu I'm trying to install. 

When I am finished it says USB contains no boot file or something like that and skips to windows 7.

Any help would be greatly appreciated. My heads spinning from this.

---

### Post by oldfred on 2010-02-04
If your BIOS does not support USB booting you cannot make it boot just by installing grub. If you have a BIOS upgrade that may help. Other alternatives are a boot floppy that has grub or supergrub to allow booting and then chooseing the USB or the same thing with a CD.

Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by LeotCol on 2010-02-04
> **oldfred said:**
> If your BIOS does not support USB booting you cannot make it boot just by installing grub. If you have a BIOS upgrade that may help. Other alternatives are a boot floppy that has grub or supergrub to allow booting and then chooseing the USB or the same thing with a CD.

Rescue CD and boot grub2 floppy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")


Original Text: "My BIOS does support USB booting."

---

### Post by oldfred on 2010-02-04
Maybe if I had learned how to read it would have helped, sorry.

With the external plugged in run this script so we can see what is installed where.

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

On my desktop the choice of booting a USB drive (it was a USB key) was not under USB, USB floppy,USB CD etc, but was under hard drives.

---

