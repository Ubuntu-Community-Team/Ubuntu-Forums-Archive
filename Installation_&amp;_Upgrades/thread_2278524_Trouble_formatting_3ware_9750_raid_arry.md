---
title: "Trouble formatting 3ware 9750 raid arry"
date: 2015-05-17
forum: Installation &amp; Upgrades
---

### Post by Andrew_Benjamin on 2015-05-17
I have installed 14.04 on a new machine

I installed a new raid card (9740-8i) and I created a RAID 5 array on 3x4TB drives which is correctly seen by the system.

I now need to partition and format the drive so that it is seen as a single 8TB (actually 7+) drive which I will share via Samba.

It's been years since I've done this and clearly I'm doing it wrong.

I ran:
```
[FONT=Consolas]parted /dev/sdc mklabel gpt
[/FONT][FONT=Consolas]parted /dev/sdc mkpart primary ext4 1 -1[/FONT]
```

I'm getting an error on the '1'

I was then going to run:
```
[FONT=Consolas]sudo mkfs -t ext4 /dev/sdc1[/FONT]
```

So, quite simply:  What commands do I run to end up with an ext4 '8TB' drive under 14.04?

Thanks, everyone.

Andrew

---

### Post by Andrew_Benjamin on 2015-05-18
Well, I installed a graphical front end and used gparted - got everything up and running more easily that way.

Andrew

---

