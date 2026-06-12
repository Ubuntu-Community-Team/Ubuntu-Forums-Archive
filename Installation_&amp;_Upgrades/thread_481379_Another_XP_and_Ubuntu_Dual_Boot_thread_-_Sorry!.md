---
title: "*Another* XP and Ubuntu Dual Boot thread - Sorry!"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by gam3r on 2007-06-22
Hey guys. I have read a few guys and run a few searches but i am still unsure on how to get this working in the way i want it to.

Right now this is my current HD/Structure:

I got 1x250gb SATA Drive which is partitioned into 3 parts: C: D: and E:

I got 1x500gb SATA Drive which is partitioned just into 1 part : H:

The 250GB hd has my Windows XP SP2 OS on it which i want to keep fully operational but i want to install Ubuntu and i am not sure weather i need a new clean drive or partition to install it to..

Can anyone enlighten me on this matter?

Thanks

---

### Post by tj.c on 2007-06-22
I have something simular. Two IDA drives. Primary = Windows c:, d:, secondary = wiped clean. I loaded Ubuntu on to the secondary IDE ( into 2 partitions, 1 for /root, 1 for /home) and let it install grub. Clean and simple. You can modify grub's menu.lst to your liken. When the pc boots, grub presents a menu of which OS to boot and defaults to the last run OS. 

If you need more detail let me know.

---

### Post by crane on 2007-06-22
YOu can do either. Install in another partition or on the other drive. It depends on which dives have data you want to keep. You will not have your hard drives represented by drive letters when you start formating  through the install. You Drives will be HDA and HDB the a number will be assigned to the partitions.
C = hda1  (hda tells you its the first hard drive and the 1 tels you its the first partition)
D = hda2  (First hard drive, 2nd partition)
E = hda3  (First Harddrive 3rd partition)
H = hdb1  ( hdb = 2nd hard drive 1 = 1st partition)

Just be sure not to format your hda1 and windows OS should be fine. As far as part partitions you want, that is a personal preference. Just be sure at a minimal you have a root directory for Ubuntu it will be labeled / and a swap partition. Make sure you have enough space to install the OS ( at least 3 -4 gig) on the swap partition size will depend on you system spec. But if you make the partition twice the size of your memory you should be OK. So if you have 512 meg ram make your swap 2 gig.

 Hope this helps.

---

### Post by Pumalite on 2007-06-22
> **crane said:**
> YOu can do either. Install in another partition or on the other drive. It depends on which dives have data you want to keep. You will not have your hard drives represented by drive letters when you start formating  through the install. You Drives will be HDA and HDB the a number will be assigned to the partitions.
C = hda1  (hda tells you its the first hard drive and the 1 tels you its the first partition)
D = hda2  (First hard drive, 2nd partition)
E = hda3  (First Harddrive 3rd partition)
H = hdb1  ( hdb = 2nd hard drive 1 = 1st partition)

Just be sure not to format your hda1 and windows OS should be fine. As far as part partitions you want, that is a personal preference. Just be sure at a minimal you have a root directory for Ubuntu it will be labeled / and a swap partition. Make sure you have enough space to install the OS ( at least 3 -4 gig) on the swap partition size will depend on you system spec. But if you make the partition twice the size of your memory you should be OK. So if you have 512 meg ram make your swap 2 gig.

 Hope this helps.

When I installed 7.04, my drives went from hda to sda,????

---

### Post by JimNSB on 2007-06-22
> **Pumalite said:**
> When I installed 7.04, my drives went from hda to sda,????

I thought sda = SCSI (SATA) drive

Are they IDE HD's?

---

### Post by Pumalite on 2007-06-22
> **JimNSB said:**
> I thought sda = SCSI (SATA) drive

Are they IDE HD's?

Ubuntu 7.04 reads hda as sda and so on.

---

### Post by fumduck on 2007-06-22
this is the guide I used which I found helpful.. But I also used search functions also on forums..

[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

---

