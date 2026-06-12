---
title: "patitions"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by TheRacerX on 2010-06-07
im having an issue my computer is an Acer Extensa 4420 it comes standard with a 160GB hard drive its split into 2 partitions the primary and the backup problem is i used the back up to install Ubuntu 9.10 and now i cant get it off the computer. So i can reformat that partition back to Windows so i can get some more storage space for my downloads and stuff how do i get rid of Ubuntu without having to reformat my entire hard drive and reinstall Windows 7?

---

### Post by darkod on 2010-06-07
Did you install with wubi inside windows or on its own ext4 partition?

---

### Post by TheRacerX on 2010-06-07
no i did a full install in the back up partition on its own in a ext3 format

---

### Post by darkod on 2010-06-07
If grub2 is on your mbr, first put windows bootloader there before deleting the ubuntu partition. After that you can simply use windows Disk Management to delete the partition(s) and create ntfs partition from that space.

Instructions to restore windows bootloader here, if you need it:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by TheRacerX on 2010-06-07
i dont think its grub2 though according to my roommate its an older grub boot manager

---

### Post by darkod on 2010-06-07
> **TheRacerX said:**
> i dont think its grub2 though according to my roommate its an older grub boot manager

OK, it doesn't matter. The point is the same.

---

### Post by TheRacerX on 2010-06-07
alright ill give it a try it better not **** up my hard drive or deny me access to my windows operating system im going to be very annoyed if i have to reformat the entire hard drive cause i have some games installed on Windows that i cant afford to lose since i had to pay for them online to install them

---

### Post by restorator on 2010-06-07
If you are not very comfortable with the procedure or concerned you will lose critical data, you should do a full backup (which is always a good idea anyway) before you attempt to do a change. Alternatively you could also locate someone locally that has more experience with this procedure.

---

### Post by TheRacerX on 2010-06-07
ill try that cause i dont feel comfortable doing it myself i have a bad track record with trying to fix software problems myself lol

---

