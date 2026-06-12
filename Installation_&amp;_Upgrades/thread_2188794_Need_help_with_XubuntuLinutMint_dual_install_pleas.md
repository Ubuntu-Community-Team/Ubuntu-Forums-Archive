---
title: "Need help with Xubuntu/LinutMint dual install please"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by marinecomm on 2013-11-19
I originally had Xubuntu 12.04 on my system and decided to dual install LinuxMint. After repartitioning and installing, everything seemed to go fine. However, when I rebooted it went straight into Xubuntu and didn't even give me a choice of the two. What did I go wrong and how can I correct it?

---

### Post by heir4c on 2013-11-19
In Xubuntu do a update of grub. Open a terminal and type:
```
sudo update-grub
``` 

Than you see something like this (This is in the Dutch language):

> gerolf@gerolf-E35M1-M:~$  sudo update-grub
Aanmaken van 'grub.cfg'...
Linux-afbeelding is gevonden: /boot/vmlinuz-3.12.0-3-generic
Initrd-image gevonden: /boot/initrd.img-3.12.0-3-generic
Linux-afbeelding is gevonden: /boot/vmlinuz-3.12.0-2-generic
Initrd-image gevonden: /boot/initrd.img-3.12.0-2-generic
Found memtest86+ image: /boot/memtest86+.bin
Ubuntu 12.04.3 LTS (12.04) is gevonden op /dev/sda3
Ubuntu 13.10 (13.10) is gevonden op /dev/sda5
Ubuntu 13.10 (13.10) is gevonden op /dev/sdb1
Ubuntu Trusty Tahr (development branch) (14.04) is gevonden op /dev/sdb2
Ubuntu 13.10 (13.10) is gevonden op /dev/sdb3
voltooid
gerolf@gerolf-E35M1-M:~$ 

You see now Mint in the list? Than you can reboot and you can choose for Mint.

---

### Post by fantab on 2013-11-19
> **marinecomm said:**
> I originally had Xubuntu 12.04 on my system and decided to dual install LinuxMint. After repartitioning and installing, everything seemed to go fine. However, when I rebooted it went straight into Xubuntu and didn't even give me a choice of the two. What did I go wrong and how can I correct it?

It is possible that you either your install didn't go well.
It is also possible that you installed GRUB from LinuxMint to its own partition.

Like the post above suggests run:
```
sudo update-grub
```

...in Xubuntu and reboot to check.
Let us know what happens.

---

### Post by marinecomm on 2013-11-19
Yes, that did the trick. Thank you.

---

