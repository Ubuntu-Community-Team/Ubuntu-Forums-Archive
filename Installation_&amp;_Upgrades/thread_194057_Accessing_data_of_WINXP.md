---
title: "Accessing data of WINXP"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by vasimakhtar on 2006-06-10
Hi
I have dual boot with Winxp and Ubuntu. How can I access data of Winxp from Ubuntu.
Thanks

---

### Post by adwait on 2006-06-10
You will have to mount the partition (search for it in the Wiki). If the partition is FAT32, there's no problem but if its NTFS, Linux will only be able to read it.

---

### Post by skelooth on 2006-06-10
you need to 'mount' your windows partition. There is a very good chance it's hda1, so you would go to a terminal and type in

> mkdir /mnt/win
> mount /dev/hda1 /mnt/win

or you can add an entry into fstab

---

### Post by nanotube on 2006-06-10
go to the third link in my sig, and go to the item on accessing your windows partitions. :)

---

### Post by vasimakhtar on 2006-06-10
-Thanks to all...Cheers I did that...UBUNTU is real fun.....I enjoyed much than winxp

---

