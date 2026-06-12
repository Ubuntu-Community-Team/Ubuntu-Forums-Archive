---
title: "Can this be resize?"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by neen2k on 2011-07-22
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=198034&stc=1&d=1311313607[/IMG]

I'm new with ubuntu and not really particular with the current situation. because extended and swap is at the last part of the disk.

---

### Post by 2F4U on 2011-07-22
I assume that it is not a LVM setup, right? Then it will be difficult to resize.

---

### Post by Quackers on 2011-07-22
I presume that you want to resize sda1?
If so boot from the Live cd/usb and open gparted then right-click on the swap partition and select "swapoff".
All partitions should then be unlocked and sda1 can be resized.

---

### Post by Elfy on 2011-07-22
That said is it worth it for less than 1Gb ?

---

### Post by neen2k on 2011-07-22
> **Quackers said:**
> I presume that you want to resize sda1?
If so boot from the Live cd/usb and open gparted then right-click on the swap partition and select "swapoff".
All partitions should then be unlocked and sda1 can be resized.

very well said... thank you @Quackers. will help out others once I got this fix.

Will update thread once dualboot is up and running..

---

### Post by dino99 on 2011-07-22
what you need:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by neen2k on 2011-07-22
I am actually planning to install win7 as a secondary OS and linux as default.

I would also want to have a partition where linux and ubuntu can access freely. ive red that ext2 does the job.

---

### Post by dino99 on 2011-07-22
ext4 is the standard used, ext3 is older and secure

---

### Post by Quackers on 2011-07-22
A partition which is shared between the two systems is usually NTFS.

---

### Post by dino99 on 2011-07-22
> **Quackers said:**
> A partition which is shared between the two systems is usually NTFS.

are you sure ?

its 21th century now :)

---

### Post by Quackers on 2011-07-22
NTFS works for me :-) And I don't trust MS writing to my ext partitions! :-)

---

