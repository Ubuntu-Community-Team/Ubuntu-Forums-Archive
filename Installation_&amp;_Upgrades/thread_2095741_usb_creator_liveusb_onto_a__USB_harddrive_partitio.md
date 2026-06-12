---
title: "usb creator liveusb onto a  USB harddrive partition?"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2012-12-17
I took a USB IDE hard drive and partitioned out a 20gb section formatted to fat32.

Then ran usb creator and it loaded onto the partition ok.

However, it does not boot, it tries, the light flashes on the drive, the monitor just blinks a cursor.

Should it work?
2nd shows gparted of the hard drive

I had to lower the persistance down to 3.5gb or usb creator gave checksum errors.

---

### Post by sdowney717 on 2012-12-17
gparted says you can use a usb hard drive
How do you determine a cylinder boundary??
[http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)
> 

TIP:   If your USB flash drive or USB hard drive is not able to boot, check the following:

    Ensure that your USB flash drive contains at least one FAT partition.
    Ensure that the partition is marked as "bootable" in the partition table.
    [B]Ensure that the partition starts on a cylinder boundary.
    For the first partition this is usually sector 63.[/B]



In my case, it is the second partition.

---

### Post by sdowney717 on 2012-12-17
Ok, deleted the partition.
Then recreated and selected to align to cylinder.
The new partition lost 2.5mb so it is different.
I am now redoing the usb creator on the drive.

Well, that did not help.

---

### Post by C.S.Cameron on 2012-12-18
As far as I know, A Live or Persistent install needs to be on the first partition of the drive and that partition needs to be FAT32.

Plop Boot manager is good at booting devices that BIOS fails.
It will run off a CD.

---

### Post by sdowney717 on 2012-12-18
I will try with a first partition liveusb and see.
What I am curious is if it will run much faster than a usb stick.

---

### Post by C.S.Cameron on 2012-12-18
My experience is that an install on an external USB hard drive runs a bit faster, (with less freezing), than on a flash drive and that USB3 hard drives run a whole lot faster.
I have not bench marked them yet but installs on my USB3 drives seem faster than on my internal SATA drives These are full installs and not persistent.

Full installs and persistent installs on flash drives always seem about the same speed to me.

Oops, to better understand, are you connecting the hard drive by USB or by SATA.
If you are connecting it internally by SATA cable, (Frugal install), it should run at about the same speed as a Full install and much faster than an USB stick.

---

### Post by sdowney717 on 2012-12-18
It is a USB 2.0 external hard drive case with an IDE drive inside.

I was using a good 300gb Maxtor drive and the ubuntu partition was number2

I tried another old 15gb drive and it workied as a first partition

This 2nd drive booted faster,
Ths drive did **a lot of clanking!**

Should it be clanking the read arm?

I suppose I can move the partition on the 300gb drive and put a small ubuntu partition on the front to test this again.

---

### Post by C.S.Cameron on 2012-12-18
> **sdowney717 said:**
> It is a USB 2.0 external hard drive case with an IDE drive inside.

I was using a good 300gb Maxtor drive and the ubuntu partition was number2

I tried another old 15gb drive and it workied as a first partition

This 2nd drive booted faster,
Ths drive did **a lot of clanking!**

Should it be clanking the read arm?

I suppose I can move the partition on the 300gb drive and put a small ubuntu partition on the front to test this again.

My experience is that once clanking starts there is not much time left and to back up now.

---

