---
title: "XP resize and Ubuntu 7.04 (GRUB question)"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-08-06
I have installed XP on a desktop (AMD).
Then I have installed Ubuntu.

The hard disk has a size of 80 GB.
Since XP did not boot anymore, I have deleted the partition and was happy using Ubuntu.

The empty space of 25 GB inspired me to partition the hard disk:
/dev/sda1    .   9 GB
/dev/sda2    .   16 GB
/dev/sda3     ... left for Ubuntu

I installed Vista on /dev/sda2 !  and lost so GRUB to select Ubuntu.
To get my /dev/sda3 Ubuntu back I installed Ubuntu on /dev/sda1 again!

Booting the system gives me now the choices to boot
Ubuntu on /dev/sda1
Vista on /dev/sda2
Ubuntu on /dev/sda3

I want to remove /dev/sda1 and replace it with XP! 

Questions:
1. How can I get the system to boot without having /dev/sda1 as Ubuntu?
2. How can I install XP on /dev/sda1 AND get it into GRUB as one of the boot OS ?

Thanks for you help!

bye

Ronal

---

