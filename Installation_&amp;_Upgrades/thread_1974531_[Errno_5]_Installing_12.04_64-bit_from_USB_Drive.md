---
title: "[Errno 5] Installing 12.04 64-bit from USB Drive"
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by ooboontwo on 2012-05-06
Hello everyone,

I am getting a frustrating error, and google is not able to rescue me.

I am trying to install Ubuntu 12.04 64-bit from a USB Drive to an internal PATA (IDE) HDD. Whie copying files I always get the error, "[Errno 5] Input/output error". The details of the error say that this is most likely a faulty Live CD, bad burn, corrupt ISO image etc. etc.

1. I have "checked the live CD (really, a USB thumbdrive) for defects" and it has not detected any.

2. I have tried preparing my HDD as ext4 w/ Gparted, and have left space unallocated, have also tried creating and selecting partitions with Ubiquity. Nothing seems to make a difference.

3. I have used Unetbootin to apply the ISO image to my USB thumbdrive several times.

4. I have tried using the command "ubiquity --no-migration-assistant" in terminal. Same error.

The Live USB Drive works great. 12.04 runs perfectly off the thumb drive itself, but it won't install to my HDD. :(

Any thoughts?

Cheers,
Cody

---

### Post by mips on 2012-05-06
try writing the image with dd or use the alternate iso image.

---

### Post by untill on 2012-05-08
Same here. Ubuntu 12.04, 64 bit, USB stick. The PC is right from the factory, so I suspect the installer.

---

### Post by untill on 2012-05-08
My workaround: Installed 11.10, then ran Upgrade.

---

