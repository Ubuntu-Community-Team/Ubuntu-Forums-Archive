---
title: "hardy start up error resume wrong partition"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by piusvelte on 2008-04-30
***UPDATE: RESOLVED***
Just after grub loads and there's a message printed stating 'Starting up...', the screen would go to a black screen with a flashing cursor. After pressing ctl+alt+f1, the errors messages can be seen:
kinit: name_to_dev_t(/dev/disk/by-uuid/XXXXX)=/dev/sdXX(x,x)
resume libgcrypte 1.2.4, device not found

To fix this:

sudo swapoff /dev/sdXX
sudo mkswap /dev/sdXX

sudo fdisk -l | grep swap
sudo vol_id -u /dev/sdXX

#correct:

/etc/uswsusp.conf
/etc/initramfs-tools/conf.d/resume

sudo dpkg-reconfigure uswsusp
sudo update-initramfs -u

***

I have to 'hand-hold' my machine starting up everytime since upgrading from gutsy to hardy. GRUB loads, 'Starting up' prints to the screen, and then there's just a black screen with a cursor. If I press ctl+alt+f1, I drop to a terminal and can see that it's attempting to resume from /dev/hda2. On gutsy, that was my swap partition, however, no all my drives are sdXX. The error says 'enter full path to device or press enter to boot normally'. If I press enter, everything goes along fine, though 'Starting NFS Common Utilities', fails the first time and takes several minutes the second time. How do I fix the resume problem? I've changed my fstab to use the new sdXX assignments, but that hasn't fixed the booting issue. Thank you!

---

### Post by Pumalite on 2008-04-30
What about UUID's? They have to coincide in: blkid. /etc/fstab, and menu.lst

---

### Post by piusvelte on 2008-04-30
> **Pumalite said:**
> What about UUID's? They have to coincide in: blkid. /etc/fstab, and menu.lst

Well, I had changed fstab to use /dev/sdXX instead of UUID, but I just changed all the hd's to UUID, using blkid. I checked menu.lst and it was already correct. I did notice that the dvd was mounted in fstab using /dev/hdc, which appears to be wrong as it's now /dev/scd0. I checked my other hardy machine and it uses /dev/scd0 in fstab, so I updated fstab.

So floppy is /dev/fd0 and dvd-rom is /dev/scd0, correct?

I'll try rebooting when I get home to see how it goes.

Thank you!

---

### Post by piusvelte on 2008-05-01
The problem still exists. I went looking around in /boot/grub, which I know is dangerous, and found the device.map file. The file contained only this:

(hd0)  /dev/hda
(hd1)  /dev/hdb
(hd2)  /dev/hdd

As hardy now labels the drives as if they were scsi, I tried changing the file to this...

(hd0)  /dev/sda
(hd1)  /dev/sdb
(hd2)  /dev/sdd

...as my other hard machine has (hd0)  /dev/sda. The problem persists, though now the error line states that it's mapping the /dev/disk/by-uuid/XXXX-XXXX... to /dev/sda(8,2), whereas before it would print hda(8,2). It still ultimately prints that it can't find the device to resume from /dev/hda2. I'm starting to think that this isn't coming from grub, but something involved in the kernel loading, post grub. blkid, menu.lst and fstab all are using the same uuid's. The messages printed are all preceded by 'kinit:'.

I think I may have just found the problem!!! The 'resume' message got me thinking, so I checked /etc/uswsusp.conf and it has the resume device set as /dev/hda2. I updated this and will try rebooting tonight when I can watch it come up.

---

