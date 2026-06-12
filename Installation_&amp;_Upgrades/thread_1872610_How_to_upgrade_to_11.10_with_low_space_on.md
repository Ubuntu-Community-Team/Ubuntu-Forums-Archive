---
title: "How to upgrade to 11.10 with low space on /"
date: 2011-10-31
forum: Installation &amp; Upgrades
---

### Post by scherrey on 2011-10-31
I've got an eeePc 901 with a fairly small root partition so there's no way I can clear up enough space to perform an in place upgrade. My home partition has enough however. Is there some option where I can tell the upgrade program to put its files somewhere else?

I guess this question applies generally to anyone with limited root partition space.

---

### Post by dino99 on 2011-10-31
you need to:

- boot with a cd/usb live system to resize your / partition with gparted: 10 Gb to be confortable (shrink /home first if you dont have free space to extend /)

- then open a terminal to list the uuids:
 sudo blkid (take note of them)
 sudo nano /etc/fstab ( update with the new uuids)

- doing this, you get new uuids of course, so grub rescue will appear on next boot. Supposing that your / partition is /dev/sda, then to get the grub menu you need to run:
1. set prefix=(hd0,0)/boot/grub
2. set root=(hd0,0)
3. insmod normal
4. normal

Activate the normal module. If successful, the GRUB 2 menu may appear. 

Now you can login again; and you need to built an updated grub.cfg:
sudo update-grub

Voila :)

---

### Post by scherrey on 2011-10-31
I appreciate the responsive answer. Unfortunately this computer has two SSD drives. One, my root drive, is only 4G and the root partition has the whole thing so expansion isn't an option. If I can't point the .deb files somewhere else I guess my only real option is a re-install and forget about upgrading. Thanx.

---

