---
title: "Help with BCM4311"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by azhtar on 2010-03-31
How can I install my broadcom BCM4311 driver without Internet connection nor installation CD?

I use to install Ubuntu using my USB memory key and copying the iso with the program UNETbootin so I don't really know how to do it without connecting the notebook to the network using an ethernet cable.

---

### Post by TBABill on 2010-03-31
I'm pretty certain you'll need the LiveCD, LiveUSB or a hard-wired connection to a router in order to pull in the drivers. Unless you have another computer with access somewhere else where you are able to copy files to CD or a USB device (HDD or thumb drive) and you are savvy enough to manually install. I'm definitely not but hopefully further responses may give better insight.

---

### Post by petejk on 2010-03-31
I have this problem when using a live cd
I have to run sudo gedit /etc/apt/source.list
comment out the sources with a # on each line, save, then run synaptic

in synaptic, on the edit menu, select add cdrom - the packages from your usb or cd will be loaded

you can then either install the wireless driver using System/Administration/Hardware drivers, or select and install the bcmwl-kernel-source package from within synaptic

hope this helps

Pete

---

