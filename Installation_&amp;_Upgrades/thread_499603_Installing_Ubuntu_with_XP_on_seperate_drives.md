---
title: "Installing Ubuntu with XP on seperate drives"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by dgcarter on 2007-07-12
Hi,

I have three HDD's a 160GB SATA (SATA port 1) HDD, a 40GB IDE (Primary IDE Master) HDD. and a 20GB IDE (Secondary IDE Slave) HDD.

The 40GB is used for windows backups etc.

I have windows on the SATA drive and Ubuntu 6.06 on the 20GB HDD

The install goes as normal, dosen't say anything about other OS's. when I boot up, it boots windows. so I changed the primary boot HDD in bios to the 20GB HDD with Ubuntu on. it loads GRUB and I get a list with the Ubuntu options and the option to boot form windows.

If i select Ubuntu I tells me it can't load the partition. if I select windows, it says NTDLR is missing.

WIndows is still ok when I change my primary boot HDD back to the windows drive.

Any ideas?

---

### Post by Pumalite on 2007-07-12
Post:
sudo fdisk -l
sudo /etc/fstab
sudo /boot/grub/menu.lst

---

### Post by dabl on 2007-07-12
You can think of that IDE drive as a "Grub Magnet" for Ubuntu.  Here's some information: [http://kubuntuforums.net/forums/index.php?topic=3083082.0](http://kubuntuforums.net/forums/index.php?topic=3083082.0)

:)

---

### Post by dgcarter on 2007-07-12
Hmmm... I see.

So I'm guessing there is no way around this... perhaps I can resize the partition in the SATA drive if I do a XP rescue.

---

### Post by dgcarter on 2007-07-12
Ok, after doing some reading I sort of go it.

I changed the /boot/grub/device.map so it reads:

> 
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/hdb


And the /boot/grub/menu.lst reads (just the windows section)

> 
title   Microsift Windows XP Professional
root  (hd1,0)
savedefault
makeactive
chainloader+1


now when I select the windows option, the screen just flashes quickly and it does nothing. what am I missing?

---

### Post by Pumalite on 2007-07-12
As dabl said there are issues with mixtures of SATA and IDE drives. The only thing I can think of at this point is for you to read up and download and burn this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

And apply the fixes that you see fit.

---

### Post by dgcarter on 2007-07-12
BAH!!! Humbug! I give.

I'll just resort to caveman technics till the problem is sorted... open PC, rip cable out... boot linux, open PC, plug cable in, rip other cable our... boot windows!!! YAY ME!!

I dnt use that PC's windows OS that much anyhoo...

---

