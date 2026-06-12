---
title: "Install with XP Help"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by aknjusa on 2007-03-08
Hello
I downloaded Ubuntu 6.06 LTS, made a CD and tried to install on a slave drive containing 2 NTFS partitions. I was aiming to make a dual boot system. The slave drive is 200GB with 2, 100 GB partitions, one of which is almost empty, 100GB.

Ubuntu install process does not show the 2 partitions. I allowed it to create a 75GB partition but it works for a while and fails with the message 'unable to create partion' or something like that.

My PC has 2 physical HDs, primary 100GB with 1 partition and the slave with 2 x 100GB as mentioned above.
How should I proceed to make a dual boot system?

---

### Post by Kateikyoushi on 2007-03-08
Then remove the almost emptry partition from windows with disk manager and then try again.
For the installation this dualboot guide might come handy. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

### Post by aknjusa on 2007-03-09
OK, I removed the G: drive (100GB) and let install proceed. Ubuntu reports hdb has 200GB and 167 is used. Should I use some old fashioned fdisk program and make Linux visible partitions? If so, can I do it from USB device? If not I will need ot make a bootable CDROM.

---

### Post by mikewhatever on 2007-03-09
Ubuntu desktop installer has a partition managing tool. Have you looked at the link posted by Kateikyoushi? Do not rush forward blindly. Make sure you know what you're doing.

---

### Post by Kateikyoushi on 2007-03-09
That does not look good, it is said that windows partitioning tools like pqmagic do not play well with ubuntu. 
The way things look now continuing the installation has a very high chance of breaking both partitions. 
I would like to figure out what causes this so please tell us about your hardware.

There is a gparted live disc which has the newest gparted (same tool what's on the ubutu live disc) I would recommend to give that a try. [LINK]("http://gparted.sourceforge.net/livecd.php")

---

### Post by aknjusa on 2007-03-10
I d/l gparted and made the CD.
It reported a 194GB or so single partition with 47GB used.
On trying to relocate the current partition to a smaller one of about 100GB , it experienced error and was trying to save the htm page. My HW is as follows.

Soyo MB, SiS chipset  with AMD 2800+ Athlon, 512MB RAM, MAxtor 6L200P0

IDE: PCI\VEN_1106&DEV_0571&SUBSYS_10FDA723&REV_06\3&61AAA01&0&89

Thanks

---

