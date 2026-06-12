---
title: "ubuntu on raid 0"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by panchopc on 2007-04-20
Hi guys first time poster here
im trying to install ubuntu
have tried desktop 6.06 lts amd4 64
and right now trying the alternate

on a dell power edge 1950
ive installed ubuntu before
but on this machine its giving me a big headache because
it has a perc 5/i controller 
im trying to install a raid 0
i have 2 140 gb hd
ive created the virtual disks on the raid bios

when i try to install ubuntu
it detects 4 partitions

hdb......... first phisical drive......(hd0,0)
hdc......... second phisical drive....(hd0,1)
hdd..........first virtual drive (hd2,0)
hde........second phisical drive(hd2,1)

i go ahead and install it on hdd
but when the installation is about to end
i notice it installs
grub at hd0
so when i boot
grub error 17 apears

so then i boot from a live cd
and install grub om hd2

so when i see my /boot/grub/menu.lst
(hd0,0)
(hd2,0)

apears

i dont know if i have to remove (hd0,0) and if i have to i dont know how

i downloaded the alternate version cause it said it to use it for raid
but i guess it is if u want raid software


does anyone know what i have to do

---

