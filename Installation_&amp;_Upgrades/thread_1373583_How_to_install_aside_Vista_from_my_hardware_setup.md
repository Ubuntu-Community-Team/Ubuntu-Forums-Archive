---
title: "How to install aside Vista from my hardware setup"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by aaaabbbb on 2010-01-05
Hi all,

I guess I have an unusual hardware setup that I'd like to install Ubuntu on but I haven't seen instructions for any process that meets my needs (yet).  Here's what I've got going:

* A desktop I'd like to install Ubuntu on.  It currently has Vista on it's one drive but I can easily repartition it to make room for an Ubuntu partition.  It's well past the min-specs but it does not have a (functional) CD drive.
* An external USB drive, FAT32 formatted, that I am not willing to wipe but has more than enough free room to install from.
* A macbook, also with plenty of room, on the local network from which I'd be willing to install.

Is there a dedicated partition install procedure I can use with this setup?  The only network install option I saw required a floppy drive (!) and the USB install instructions I found wanted to reformat the drive.

If there isn't then I suppose Wubi is an option.  This partition only needs to last about 4 months anyway before the machine goes 100% Windows 7 or Ubuntu (I'm trying it out).

Thanks for any help you can spare...
- D

---

### Post by gordintoronto on 2010-01-06
Another option is to use a USB flash drive.  See "Installing Ubuntu on USB drive using Windows" on this web page:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=(windows)|(flash)|(drive](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=(windows)|(flash)|(drive))

I think it is best if you have a 2 GB flash drive.  It will only work if your computer can be set to boot from a USB drive.

Yet another option is to install VirtualBox under Windows, then install Ubuntu "inside the box."  This installation can be done from an ISO.

---

### Post by aaaabbbb on 2010-01-06
VirtualBox.  Thats a fantastic idea.  Totally missed that option.

A few seconds with google brings up this butt-simple tutorial on VirtualBox sporting Ubuntu on XP:
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

I'll follow that and install from there.  Thanks!

- D

---

