---
title: "xubuntu 12.04 entry missing in grub"
date: 2014-01-04
forum: Installation &amp; Upgrades
---

### Post by johnrhenspimentel on 2014-01-04
Ok, i've just created an account here because this problem is starting to **** me off

I've installed xubuntu 12.04 from a live usb onto my /dev/sda4 partition (using ext4 filesystem and has no swap) everything seems to work great
until i rebooted.

Grub only shows memtest and windows entry, no xubuntu or linux one.

Please someone help me

Thank you

---

### Post by Bucky Ball on 2014-01-04
Welcome.

Linux one? Not sure what that is. Are you sure Xubuntu is installed and you weren't running it from the USB dongle? (Might be silly question but worth asking). When you reboot, is the USB stick in or out? If you boot with it in, do the options reappear?

If you boot from the USB dongle, get to a desktop and open Gparted you should be able to make sure that Xubuntu is actually installed on the internal hard drive at sda4.

---

### Post by johnrhenspimentel on 2014-01-04
yes. i'm sure it is installed and i'm booting from my hard drive

---

### Post by sudodus on 2014-01-04
Welcome to the Ubuntu Forums :-)

I think an installation of Ubuntu based flavours wants a swap partition, not only a root partition, but then you must repartition the drive and replace parttition number four by an extended partition. Inside that extended partition you can create any number of logical partitions, in this case a big ext4 partition for Xubuntu and a small partition for swap. If you intend to hibernate, swap should be at least as big as the RAM in GibiBytes, otherwise it might be enough with 512 MB or 1 GB.

You can do the repartitioning with Gparted when booted live from the Xubuntu install drive 'Try Xubuntu without installing'. And then try to install again.

---

### Post by johnrhenspimentel on 2014-01-05
Could it be ? i'll try what you said and will post back the result

---

