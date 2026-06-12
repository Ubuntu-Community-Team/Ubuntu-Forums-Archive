---
title: "Setting up software RAID5 on top of LVM"
date: 2017-11-14
forum: Installation &amp; Upgrades
---

### Post by Daniel_Minnaar on 2017-11-14
I have a bunch of various sized drives lying around, and decided to use them as a RAID5 array. When I created the array with mdadm, the capacity of the array was a mere 400GB, which I soon realized was a result of the smaller disks in the array.

I then decided to use LVM to combine a few of the smaller disks into a single, large volume, so that I had a more consistently sized array. After creating the volume group and physical volume, I recreated my RAID5 array. Success, capacity was now at 2TB. But then I rebooted my machine and all hell broke loose.

Doing a fdisk -l revealed that both my array, volume group and logical volumes were missing. All I could see were the original physical disks I started with. lvdisplay and pvdisplay didn't find anything. I found a backup file for the volume group but when I tried to restore it the uuids weren't corresponding to the disks and that failed.

What did I do wrong? Is it even possible to achieve what I'm trying to do here, or did I just learn a hard lesson? I've read up on articles creating the array and then setting up LVM but not the other way around, so now I'm skeptical :(

---

### Post by Tadaen_Sylvermane on 2017-11-14
Dont think its possible. What are you planning on storing? If media you may be better served by by using mergerfs to pool the drives and snapraid to provide the redundancy layer.

---

