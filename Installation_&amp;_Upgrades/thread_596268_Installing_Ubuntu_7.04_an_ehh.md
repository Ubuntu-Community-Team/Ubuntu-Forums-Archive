---
title: "Installing Ubuntu 7.04 an ehh"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by Lockyy on 2007-10-29
So ive downloaded and burnt my ubuntu livecd, all working happily from it, so as id rather not install to my internal hard drive id prefer to install it on my 500gb external hard drive.

First, is it possible.

second, how can i find out if my bios can boot from a usb ehh?


Thanks for any help! :)



*btw the title should be ehd instead of ehh*

---

### Post by rowanparker on 2007-10-29
You've just downloaded it? As 7.10 has been released recently.

1. Yes, you can install Linux anywhere. Just select the drive (and partition) which will most likely be /dev/sda#
2. Go into your BIOS, under the boot order selection screen see if it lists USB device or anything similar?

---

### Post by Lockyy on 2007-10-29
The livecd ive got is 7.04, my internet connection is rubbish and would take ages to re-download it so does it matter if im using an older version

---

### Post by rowanparker on 2007-10-29
> **Lockyy said:**
> The livecd ive got is 7.04, my internet connection is rubbish and would take ages to re-download it so does it matter if im using an older version
I understand. Don't blame you.

Were my other answers any assistance?

---

### Post by Lockyy on 2007-10-29
Yes they did, been looking on the internet but couldn't find a definite answer, saved tonnes of time :)

---

### Post by rowanparker on 2007-10-29
> **Lockyy said:**
> Yes they did, been looking on the internet but couldn't find a definite answer, saved tonnes of time :)
That's good to know :)

---

### Post by Lockyy on 2007-10-29
Just started to partition and got this error

migration-assistant needs to mount a partition, but cannot do so because the following mount point could not be unmounted:

/dev/sda1

Please close any applications using these mount points.

What do i do?

---

### Post by rowanparker on 2007-10-29
Does the drive have important data on it?
How is it partitioned? (sudo fdisk -l)
And to get rid of that error run: 'umount /dev/sda1' but make sure you don't have any open documents on it or anything.

---

### Post by Lockyy on 2007-10-29
Realised it was gaim that was making the error, closed it and the partitioning continued.

---

### Post by rowanparker on 2007-10-29
> **Lockyy said:**
> Realised it was gaim that was making the error, closed it and the partitioning continued.
Ah, goood.

---

