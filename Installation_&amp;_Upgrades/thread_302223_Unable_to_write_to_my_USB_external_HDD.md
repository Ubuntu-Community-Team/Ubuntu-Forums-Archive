---
title: "Unable to write to my USB external HDD"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by tobaccoman on 2006-11-18
:) Hi!

It is now more that 2 hours that I'm looking around on the web to solve this issue, but it looks like that I'm too stupid!

The point is the following:

I simply plugged in a USB HDD into my PC running Ubuntu

I formatted this disk before on windows as ext3 with partition magic

Ubuntu saw it immedialty displaying an icon on the desktop.

But impossible to wrtite to it.

SO I typed:

sudo chown -R root:daniel /media/
sudo chmod g+w /media/

(my username is daniel)


No error messages, but also no changes in the permissions...

How can I make it work??

---

### Post by PartisanEntity on 2006-11-19
I have the same problem, only my usb harddisk is in ntfs fileformat. Hoping someone will post here with a solution.

---

### Post by andreas64 on 2006-11-19
Hi,

o.K. two different problems:

@tobaccoman

try sudo chmod 777 /media/usbdisk ( ...if your disk is called 'usbdisk')

@PartisanEntity

it is not possible to write to ntfs-partitions. Some people are working on this, but there are only experimental driver availible.

Andreas

---

### Post by PartisanEntity on 2006-11-19
andreas64,

Thank you, now I understand. What's the most common filesystem to use and what are the limitations?

---

### Post by andreas64 on 2006-11-20
Hi,

it depends on what you want to do. If you want to share data between Linux and Windows, use FAT32. Both (Linux and Windows) can read and write on FAT-Partitions.

HTH
Andreas

---

