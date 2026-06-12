---
title: "Ubuntu dapper drake won't boot after install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by peef on 2006-06-05
Hello all,

I did an install without any problems but the system won't boot.
"Waiting for root file system"

I've got a special IDE chipset on my Asus motherboard that i know wasn't working under badger. It's an ITE 8212F chip. I'm using it in standard IDE mode.

Any advice?

PS: when i wait long enough, i've got a busybox prompt appearing.

---

### Post by peef on 2006-06-05
I tried to edit the root=... in grub because i saw some people had a problem with that.

I tried /dev/hda1, hdb1, hdc1, hdd1, sda1, sdb1, sdc1, sdd1

no one works.

Is there a command to see what devices are available under grub ?
Is there a paramater I should add to support the ITE8212 chipset ?

The weird thing is that the installation went fine. So my drives are recognized by the liveCD but not by the installed system.

Plz i'm looking some advices.

Thx

---

### Post by igul222 on 2006-07-09
i have the same problem. I don't think it's your ITE8212, as other people seem to be having that problem too. I've tried disabling the ITE8212 altogether from the BIOS, and connecting the hard drive to the CD-ROM cable instead. Same error. What motherboard are you using, because it looks like a problem with the motherboards.

---

### Post by peef on 2006-07-17
My motherboard is an Asus P5GD2.

---

### Post by atrophic on 2006-07-17
> **peef said:**
> Is there a command to see what devices are available under grub ?

/boot/grub/device.map has the list of devices grub knows about

---

### Post by Donk^^ on 2006-07-28
Subscribes to this bug:
[https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197)

---

### Post by peef on 2006-07-29
Many thanks to you, it worked for me.

Hope it will do the trick for the other people too.

:D

---

