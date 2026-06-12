---
title: "Create USB startup disk........"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by GmAz on 2008-10-31
I want to create a USB startup disk, but I want to make it exactly how my system is right now.  Is there a way to 'repackage' my current Ubuntu install into an ISO file so it can be put on the USB flash drive?

---

### Post by Huss on 2008-11-18
That makes two of us. ...

---

### Post by C.S.Cameron on 2008-11-18
If your current system will fit onto a flash drive you can use dd to clone it to the flash drive.

dd if=/dev/sda of=/dev/sdb

Before proceeding confirm that sda is the disk you wish to clone from and sdb is the partition or disk you wish to clone to.

This ends up as a Full install and not just an image.

---

### Post by Huss on 2008-11-19
Great, thanks!

Do you have to specially format the drive first?

Also, is it possible to pick and choose the apps you want bought across?

---

### Post by C.S.Cameron on 2008-11-19
All I've used dd for is cloning entire disks, bootable flash drive to flash drive and to hdd.
It clones the formatting as I have cloned disks with multiple partitions.
I understand that you can get it to leave out empty space when copying, but am not sure of the code.
Also not sure about being able to only choose certain apps.

You might also want to check this out, I've not tried it yet:

[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by Huss on 2008-11-19
Hmm, I'll look into it

---

