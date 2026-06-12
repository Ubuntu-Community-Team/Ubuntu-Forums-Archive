---
title: "severe fstab problem in edgy"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by lugburz on 2006-10-25
Hi,
I upgraded my good kubuntu dapper with this orrible edgy, the main reason of instability seems the fstab and the use of the volume ids, not very stable.

The first problem happened because the uuid for the swap partition, changed after that I try to hibernate my laptop.

The second problem was when to system was unable to mount my home directory, realy I found that my fstab was empty and I don't know why.

The edgy version seems like windows: do strange things without any explanation.](*,)

---

### Post by lugburz on 2006-10-25
I try to explain better:

after a normal reboot the system was unable to mount /home partition, reading the fstab I see that this file contain only two line: one to mount the swap partition and another to mount the cdrom, no command to mount / or /home or the other important directories.

Where is the problem?

I temporary solve this problem using the old fstab created in dapper, leaved in /etc directory after the upgrade to edgy whit the name: fstab.pre-uuid

---

