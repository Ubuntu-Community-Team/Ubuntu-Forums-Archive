---
title: "How do I resize device and partition?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Brian_G_M on 2010-06-29
Hi
I have Ubuntu on an ASUS EEE netbook. I tried to upgrade to 10.04 LTS, but I get a message that I need more disk space. My disk is set up with 2 devices, dev/sda1, sda2; and dev/sdb1. I have space in sdb1, but  I don’t know how to increase sda and reduce sdb. GParted seems to resize partitions within devices, but how do I resize a device?

Thanks for your help.

---

### Post by kalistona on 2010-06-29
sda means your first disk.sdb another (usb ?), gparted is the right tool. 
you must resize the partition where is your ubuntu 10 but **you'r going to loose all** !
so you have not really [COLOR=Blue]make a good install[/COLOR] of your ubuntu on the second partition or on the other disk.  
[COLOR=Blue]reinstall your ubuntu[/COLOR] and **choose .iso 10** please.(i do not know if it is supported ...)

---

### Post by Brian_G_M on 2010-06-29
sda (4Gb) and sdb (16Gb) are both on my "hard disk" (20Gb), they are set up as two separate devices.

---

### Post by regala on 2010-06-29
> **Brian_G_M said:**
> sda (4Gb) and sdb (16Gb) are both on my "hard disk" (20Gb), they are set up as two separate devices.

eeepc 90x have 2 hard drives. One is 4G long, the other 16G.

a device has a _physical_ size. You can't "exchange" space between devices. /dev/sda will forever be 4G, in this EEE pc. Unless you open it, and put a 8G hard disk.


or you can try to reinstall Lucid using an lvm setup when you are asked to partition the disks, prior to install.
but in your very setup, you can't do what you ask, unless you reinstall completely ubuntu.

---

### Post by Brian_G_M on 2010-06-29
Thanks Regala, I didn't realise, I thought I had one unit of 20GB.
So in that case how do I upgrade to the latest Ubuntu? I guess it installs the new version before it deletes the old one, so needs a lot more space than the original installation.

---

### Post by dino99 on 2010-06-29
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

