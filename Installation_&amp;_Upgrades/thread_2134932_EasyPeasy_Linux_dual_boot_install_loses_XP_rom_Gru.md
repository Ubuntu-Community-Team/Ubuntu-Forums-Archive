---
title: "EasyPeasy Linux dual boot install loses XP rom Grub menu"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by evilv1951 on 2013-04-12
Hi.

I am a Linux beginner, although I have messed about with a couple of dual boot XP linux installs on my Eeepc 1000HE before. I am easily stumped though.

I ran UBUNTU 11.04 quite successfully on the eeepc a while back but it all went pear shaped when I allowed it to upgrade to 12.04 last year. I won't dwell on those problems, but the trackpad vanished in the upgrade and so did the wireless network.

Today hoping to get back into Linux, I made an EasyPeasy usb boot 'disk' and all ran well. It REALLY suited the little netbook and looked great, so I installed it on the disk using the dual boot option. 

The EASY PEASY stuff runs great, BUT......

Grubt nolonger shows XP as a boot up option. I can boot the old 12.04 Linux or EASYPEASY, but no XP option appears.

Now I think I have heard of this before, but don't know how to edit the Grub menu. I've looked at the 'E' options in grub, but there is no option to add another line that I can see.

The NTFS partition is still there for sure. I called it up in the Terminal programme. It is just missing in the Grub menu.

The Grub version is V1.98 1buntu5.

Can anyone advise how I can add the XP option in Grub? I am sure it is possible, and I do need to run some XP stuff so I need to resolve it.

Many thanks to all who read and attempt to solve the problem.

---

### Post by Routhinator on 2013-04-12
Have you tried simply running:

```

sudo update-grub
sudo grub-install /dev/sda

```

This should redetect your partitions and resintall the bootloader to the first disk's MBR. If you don't want the grub loader on the MBR, run:

```
sudo grub-install /dev/sda1
```

---

### Post by evilv1951 on 2013-04-12
> **Routhinator said:**
> Have you tried simply running:

```

sudo update-grub
sudo grub-install /dev/sda

```

This should redetect your partitions and resintall the bootloader to the first disk's MBR. If you don't want the grub loader on the MBR, run:

```
sudo grub-install /dev/sda1
```

Fantastic. Thanks for that excellent solution. I ran those lines in a terminal and all works fine  now. Isn't the Internet community a great thing? I think so. You express a problem and someone from the other side of the planet comes back with a solution a couple of hours later.

Thanks again. I owe you a beer!

:)

---

