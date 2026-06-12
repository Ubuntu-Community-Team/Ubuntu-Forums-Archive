---
title: "Limited Installation Options"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by guyver on 2007-08-28
Let me start of by listing my constraints of a friend's notebook:

1.  Internal CD Drive no longer works

2.  Notebook's BIOS does not support booting off of USB Mass Storage Devices

3.  System has 128MB of RAM

4.  System does have access to floppy, ethernet, and external USB CD drive.


It is desired to make this notebook a 100% linux box so there's no partition issues to be concerned over.  

As I see it, I can either do a floppy boot and initiate a network installation of Xubuntu / Ubuntu.  Or I floppy boot and hopefully have access to the USB external CD drive and start a Ubuntu installation from there.

My other option is:  [http://www.thisiscool.com/fcfloppy.htm](http://www.thisiscool.com/fcfloppy.htm)

But I would rather do Xubuntu / Ubuntu first if possible.  Does Ubuntu have a floppy boot installation option like this or is Fedora Core the better solution to this problem?

---

### Post by bobbybobington on 2007-08-28
I would start with a straight up cd install using the usb cd drive.

---

### Post by guyver on 2007-08-28
Is there a way to do a "straight up CD install"?  I cannot boot off the CD drive.  The original internal CD drive no longer works and I cannot boot off the external drive because the notebook does not support booting off of USB mass storage devices.

---

### Post by ajgreeny on 2007-08-28
Get a copy of **smartboot manager** and put it on a floppy, instruction at the web site.  You can then boot to the floppy and from that chose to use the external CD as your boot device.  This may sound like gobbledegook at the moment but if you try it I think you'll see what I mean.

HOWEVER!  128 MB ram is not enough for ubuntu and unless you increase that to at least 256 I would suggest xubuntu.or even one of the better known lightweight distros, eg DSL

---

### Post by guyver on 2007-08-28
I tried this before and SBM did not know the external drive was present.

---

