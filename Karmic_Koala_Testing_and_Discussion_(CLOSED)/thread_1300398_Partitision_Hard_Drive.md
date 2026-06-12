---
title: "Partitision Hard Drive?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by williejones on 2009-10-24
I let Karmic live CD use my whole drive while it formated and loaded.
My drive is 20G.  I want to have my home folder on a separate
partition.  Can I do this now, or do I need to reinstall? Also, what
would you recommand for the size.

---

### Post by ranch hand on 2009-10-24
Reinstall would be easiest.

I do not know how much ram you have so you need to adjust for that, but about 8Gb for root and the rest for home.

You could use less for root but drives do slow down when too full.  That is a small drive but I have got 8.10 on an old HP with a 10Gb drive and 512Mb ram.

You will be fine.

---

### Post by williejones on 2009-10-24
Thanks Ranch Hand

This is an old Compaq Presiero that was running Windows Me that I am trying to keep from going to the dump.  It has 356 MG ram, no ethernet port, so I had to buy a USB wireless adapter which took me about a week to get working. I just want to be able to refromat withaout losing my data.  I have had to reformat  while upgrading from Jaunty to Karmak because an upgrade lost my internet connection.

---

### Post by ranch hand on 2009-10-25
RW CDs are your friend.  Back up your data and reformat.

If you start messing with your partitions and separting things you risk loosing it all anyway and will have a nightmare figuring out your fstab.  On that size box there can't be too much that you need to backup.

If you have a DVDrom you could use RW DVDs.

Two partitions are worth having to help avoid this in the future but now is  now and you really should back up and reformat.

I would use about 750Mb for swap, no less than 500Mb.

Made sure you get your wireless configuration stuff on disk.

---

### Post by williejones on 2009-10-25
Thank you Ranch Hand,

I have my wireless USB driver on CD, there is nothing elese to back up as I have just reformated.  I am thinking about waiting for the final release in case it adds something that is not upgraged, then using 9MB for home, 1MG for swat, and 10MG for home all on different paritions.

---

### Post by ranch hand on 2009-10-25
Sounds like a plan but I think we are about as stable as it is going to be for some time.

I would download a daily build CD so that it is more up to date than the RC CD;
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by VMC on 2009-10-25
> **williejones said:**
> Thank you Ranch Hand,

I have my wireless USB driver on CD, there is nothing elese to back up as I have just reformated.  I am thinking about waiting for the final release in case it adds something that is not upgraged, then using 9MB for home, 1MG for swat, and 10MG for home all on different paritions.

Do you have any external devices to keep your backups on? You need to invest in something for sure. 20g isn't much to work with. usb thumb drives are fairly inexpensive now days.

---

### Post by ranch hand on 2009-10-25
+1

---

