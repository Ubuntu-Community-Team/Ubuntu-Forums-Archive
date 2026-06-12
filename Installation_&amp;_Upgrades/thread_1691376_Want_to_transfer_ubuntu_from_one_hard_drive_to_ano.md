---
title: "Want to transfer ubuntu from one hard drive to another"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by krunalpatel on 2011-02-19
I have ubuntu installed on one hard drive (laptop hard drive). The hard drive has some bad sectors on one of the partitons. I have installed a new hard drive and now wan to import the ubuntu installation on the new hard drive. What is the easiest way of doing this? I dont' want to start fresh because I have a lot of custom drivers and settings saved.

---

### Post by slooksterpsv on 2011-02-19
> **krunalpatel said:**
> I have ubuntu installed on one hard drive (laptop hard drive). The hard drive has some bad sectors on one of the partitons. I have installed a new hard drive and now wan to import the ubuntu installation on the new hard drive. What is the easiest way of doing this? I dont' want to start fresh because I have a lot of custom drivers and settings saved.

You can download a live cd called Clonezilla which will allow you to do device-to-device cloning.

---

### Post by Z.K. on 2011-02-19
> **slooksterpsv said:**
> You can download a live cd called Clonezilla which will allow you to do device-to-device cloning.

device-to-device may not work unless both drives are the same size.  At least I was unable to get it to work.  I would suggesting copying the partition to an image using clonezilla and then restoring it to the larger hard drive.

---

### Post by slooksterpsv on 2011-02-19
> **Z.K. said:**
> device-to-device may not work unless both drives are the same size.  At least I was unable to get it to work.  I would suggesting copying the partition to an image using clonezilla and then restoring it to the larger hard drive.

You're right I don't think that will work... I can't remember, I keep thinking after I did it I had to use like gparted or fsck to fix the drive to get the rest of the space... been too long.

---

### Post by Hedgehog1 on 2011-02-19
I need to do the same thing (a few bad sectors on the 640 gig drive, moving data to new 1tb drive)

The limitation of clonezilla about different sized HDD is:

*The destination partition must be equal or larger than the source one*.

So I know it will work for me - and I hope for the OP as well.

---

