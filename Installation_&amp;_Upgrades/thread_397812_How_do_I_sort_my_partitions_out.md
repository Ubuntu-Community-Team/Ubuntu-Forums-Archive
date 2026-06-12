---
title: "How do I sort my partitions out?"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by Bigsy on 2007-03-31
Heres the problem: [http://bill.hedworth.googlepages.com/partitions.png](http://bill.hedworth.googlepages.com/partitions.png)

Unfortunately I installed this on vmware when I didnt know anything about linux (I still don;t really), but the install has slowly grown to a point that it would be a lot of work to start again.....but I need to sort my partitions out.

Whats the best way to tackle this? I want to use the full 100gb

---

### Post by zdude on 2007-03-31
A lot depends on what you want to do with the space. If you just want more misc disk space then use fdisk and add another partition. Once the partition is created you then format it, using mkfs (select which format you prefer, ext2/3, ReiserFS, XFS, etc) and lastly, mount the new partition (update /etc/fstab to automount the device).

---

### Post by andi on 2007-03-31
i don't think that you can sort your partitions after creating them.

you can create more logical partitions (sda6, sda7, ....) in the extended partition. then move for example your home and usr directories to them. since all software is installed in usr and all of your data is in your home directory this is where you need the most space anyway.

i would create a two partitions with 30GiB and 40GiB. to the first one you can copy the contents of your home directory and to the second the contents of usr. then mount them to the /home and /usr mountpoints and look if everything is okay. if it is unmount them again, delete all of the data in /home and /usr and then mount the partitions again. don't forget to edit /etc/fstab accordingly.

enjoy your 100GiB :)

---

