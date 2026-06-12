---
title: "How to uninstall windows 7"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by tyrosebush on 2012-01-05
I recently installed Ubuntu onto my Vaio X series notebook using Wubi. Everything works fine except I can't figure how to get rid of windows. I don't have enough space for both. Currently I have a dual boot where giving me the choice between the two operating systems. Thanks.

---

### Post by darkod on 2012-01-05
Wubi is an installation inside windows, so you can't remove windows but keep wubi.
What you need to do is create an ubuntu cd or usb stick, boot with it and install it on the whole disk (if you are SURE you want to remove windows).
During the install you can simply select Erase and use disk option and it will erase the disk and use it all for ubuntu.
Make sure you copy any data you need first.

---

### Post by ottosykora on 2012-01-05
> **tyrosebush said:**
> I recently installed Ubuntu onto my Vaio X series notebook using Wubi. Everything works fine except I can't figure how to get rid of windows. I don't have enough space for both. Currently I have a dual boot where giving me the choice between the two operating systems. Thanks.

you installed linux with WUBI

the wubi install is just in a virtual drive, which is simply a file (or files) ***inside*** your windows installation.
Removing windows means therefore also automatically removing the linux, nothing will be left after that, your computer will be just empty hardware then.
So as long as you have a wubi install, you can not have what you want.

You need first to create separate partition for the linux, best also a separate partition for the /home folder and some small swap partition perhaps.
There exist a procedure to transfer the wubi install to such partition, but I would suggest you do a proper new install, saving your documents and other personal data to some external storage for example. 

Then you can partition your drive and install linux into those partitions.
You can also select from the installer that you want use the whole disk, this will then take care of the rest.


--

OK, Darko was faster then me ;-)

---

### Post by tyrosebush on 2012-01-05
Thanks!

---

