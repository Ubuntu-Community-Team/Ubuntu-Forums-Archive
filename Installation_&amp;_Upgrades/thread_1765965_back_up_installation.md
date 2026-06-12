---
title: "back up installation?"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by hgjybrandon on 2011-05-23
hi , unfortunaly ububtu 10.10 crashed on both my laptops, and there too old to run 11.04,  on my desktop there's ubutnu 10.10, can i backup the files on my desktop and install them on my laptop?.. as an os, and everything?
- helps is needed, and valued-

---

### Post by Hedgehog1 on 2011-05-23
You have several options for reinstalling 10.10.

Using your 10.10 LiveCD/LiveUSB, you can boot youR laptop from it and then copy data your data from your laptop to an external hard drive or large USB stick.

**OR** - When you are booted from the LiveCD/LineUSB, you can try accessing your Desktop using the network. If you can reach it, you could copy yours files to the desktop that way.

**OR** - Another option is to use a separate '/home' partition on your laptop, so you can reinstall without hurting your data. If you have your data in a separate '/home' partition you can reinstall 11.04 over your 10.10 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE OR A REINSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by hgjybrandon on 2011-05-24
thank you, what program do i use to back up the files on a usb?

---

### Post by Hedgehog1 on 2011-05-25
If you boot from an Ubuntu LiveCD/LiveUSB, and select 'TRY', you get a fully function Ubuntu install.

From this you can run Nautilus from the 'Places' menu:

[IMG]http://img546.imageshack.us/img546/5255/screenshotnatu.png[/IMG] 

And copy your files from the hard disk to your external disk.

***The Hedge***

:KS

---

