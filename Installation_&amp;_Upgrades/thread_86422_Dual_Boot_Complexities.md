---
title: "Dual Boot Complexities"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by linuxpimp on 2005-11-05
Hi all

I have been asked to install Ubuntu into the following existing environment:

3 Partitions, 2 HD's:
P1) Windowz XP c drive FAT32 (HD1)
P2) "Other Linux", complete partition is /, no swap partition (HD1)
P3) Windows E (HD2)

What i would like to do is simply install Ubuntu over the /dev/hda5 which is in fact another Linux distro with screwed partitioning.

How will the Ubuntu installer handle this? I am apprehensive about trial and error as there is alot of business records on both Windows C and E drives that would not be good if i lose any data.

Thanks all

LinuxPimp

---

### Post by adwait on 2005-11-05
You can safely install over hda5, since it will automatically format it during installation. If you want to create a swap partition then you will have to select manual partitioning and then delete the hda5 partition and make appropriate partitions. In any case, I doubt there is anyway you can lose the data on the windows drive, nevertheless it best to make a back up, if possible.

---

### Post by linuxpimp on 2005-11-07
Thanks!

I'll let you know how it goes next week.

This is just another attempt to bring a Window$ userto the 'other side!'

LP

---

