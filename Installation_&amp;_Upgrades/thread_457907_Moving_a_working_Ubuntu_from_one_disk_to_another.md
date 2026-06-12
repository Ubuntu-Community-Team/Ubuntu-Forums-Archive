---
title: "Moving a working Ubuntu from one disk to another"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by siddartha on 2007-05-29
Hello,

I have two old hard drivers which are about to go out becase of old age. Both of them are IDE drives. I have a Feisty distribution in place already tuned and using it since December 2006. Now, I would like to avoid installing from CD. I already tried it with the normal CD and it breaks, maybe it is because I have an external drive and not a regular IDE conected inside the box.

I finally bought a new SATA II drive so the names of the drives won't be the same. Also, because it was planned only as a temporary solution the configuration in use has only one large partition for everything and a swap partition and the second old drive is used to provide just extra storage. The new drive has enough space so I would like to give separate partitions for /usr /var /home and even /boot

What can I do to move everything I have now on this only root partition to the appropiate space and also make it boot all the way. After the copy is done I would remove the old drives and put them also into external inclosures and keep them only for archiving less important things.

Cheers,
Sidd

---

### Post by Bigdog60 on 2007-05-29
There really isnt much that you can do man, it is hard to get stuff off of old hardrives especially when you are trying to take the operating system off. I would just personally forget about them and just get rid of the old hard drives.

---

### Post by blacksadness on 2007-05-29
partition the new harddrive the way you want it, and mount it under /media/disk and /media/disk/whatever then simply copy over the drive to /media/disk with after that go into your new fstab (at /media/disk/etc/fstab) and change hda / hdb to sda which is sata the only step left is to set up grub properly which is not hard to do i just forgot how :P but i think gentoo.org had sth in their handbook about manually setting up grub just follow that.. i dont' see why the copy shouldn't work.. i did it beofre, and i was copying over 2 machines and it worked..

---

### Post by siddartha on 2007-05-29
Thanks, it seems it might work. I would post the results later on.

---

