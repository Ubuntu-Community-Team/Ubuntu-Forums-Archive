---
title: "Install ubuntu on a hardisk as non persistent OS"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by KayGenz on 2010-01-16
dear all

i want to ask, its is possible to install ubuntu in a harddisk as a non persistent environment?
i mean, i want my ubuntu is always clean everytime it is restart, like a live usb.

if it possible, how to achieve that? :(

---

### Post by C.S.Cameron on 2010-01-16
Not totally sure, have not tried it but you should be able to install to a pendrive using usb-creator or unetbootin then clone the pendrive to hard drive using dd, (dd if=/dev/sda of=/dev/sdb)
You should only require a one gig partition.
You can add a casper-rw partition if you want to save some changes. You can add a home-rw partition if you want a home folder.
I'm interested in how it works out for you.

---

### Post by KayGenz on 2010-01-17
Thanks CS.Cameron for your reply.. i will try it first, i will put the result here later :popcorn:

---

### Post by C.S.Cameron on 2010-01-17
Forgot to mention that you should run dd from the Live CD or from a Live USB.

---

### Post by velosprinter on 2010-01-27
Was anyone successful at this? I would also like to have a non corruptible HD install. I do see some issues with things like security updates etc would require you to remaster the USB and DD the HD again. Chromium-OS is doing something like this in their Ubuntu variant but I am not sure exactly how that works.

---

### Post by dabl on 2010-01-27
Although this was written for a USB thumb drive, it could also be done exactly the same with a hard drive (internal or external):

[http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

It does not go through the steps of how to mount the ISO image and copy the files to the target partition, but Google will show you how to do those things.

---

### Post by snowpine on 2010-01-27
If you prefer a GUI solution, [Unetbootin ]("http://unetbootin.sourceforge.net")will do the trick.

---

