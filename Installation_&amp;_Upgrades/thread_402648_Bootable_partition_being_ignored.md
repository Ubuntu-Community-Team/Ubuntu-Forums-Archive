---
title: "Bootable partition being ignored"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by Falius on 2007-04-06
I installed Edgy Eft (6.10) on an acer aspire 5600 laptop. I partitioned my hard drive into 3 pimary and one extended, two fat32 at the start for windows and the recovery, 1 23GB ext3 bootable partition for Ubuntu, a 2GB swap space and a 7GB fat32 osshare.
I installed GRUB to the linux partition at (hd0,2) but now each time I restart the machine the Realtek Boot agent automaticly loads win XP without any options screen.
Hopefully one of you nice people can help me, as you can expect new to linux in general (ie go slow).
Cheers
Daniel

---

### Post by LowRadio on 2007-04-06
install bootloader on (hd0,0)

---

### Post by Najand on 2007-04-06
Use live cd and then mount your Linux partition using:
```

$ sudo mkdir /mnt/ubuntu
$ sudo mount -t ext3 /dev/hda3 /mnt/ubuntu

```
Then install grub again on it:
```

$ sudo -s
# grub-install --root-directory=/mnt/ubuntu /dev/hda

```
if you get no error, then restart your computer and see if it works.

---

### Post by Falius on 2007-04-06
Worked like a charm, bootloader showing all operating systems.
Thanks a lot :)
Daniel

---

### Post by Najand on 2007-04-06
Nice to hear that.

---

