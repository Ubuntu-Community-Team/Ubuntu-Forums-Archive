---
title: "Can't make a partition"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by mb107 on 2008-02-08
I'm trying to install Ubuntu from the Live CD,but I stop at Step 4.

At the **"How do you want to partition your disk?"** dialog box,
I choose the first option **"Guided - Resize SCS1(0,0,0) partition #1(sda) and use freed space"** and set it up at 15% (10.9GB).

When the **"Resizing Partition" **window appears,it doesn't progress beyond 0% and I get the **"Resize Partition failure"** message.
It says: **''An error occurred while writing the changes to the storage device.The resize operation is aborted."**.

So I can't make a partition and so I can't install Ubuntu as I want to keep my Windows XP SP2.
My hard disk is a **75GB WDC WD800JB**.

I would appreciate any kind of help.
Thank you

---

### Post by zvacet on 2008-02-08
[Here](http://www.psychocats.net/ubuntu/installing) you will find all informations you need for install.

---

### Post by Pumalite on 2008-02-08
It's better to use Gparted Live CD to resize XP: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Right click on XP, choose 'resize' from the menu.
In the new space created, make 3 partitions:
10 GB for '/'
1 GB for /swap (except laptop, where /swap must equal RAM)
The rest for /home
Install Ubuntu, go Manual and use the partitions already made.

---

