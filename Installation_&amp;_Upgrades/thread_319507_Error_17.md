---
title: "Error 17"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by natoodo on 2006-12-15
Hi, I installed Ubuntu 6.10 late last month. Had no problems with it until I updated it yesterday. After installing updates I needed to reboot. After the grub menu came up( I have Windows Xp and Vista RC1 on separate partitions. My HD is partitioned in 3.)
I selected Ubuntu and pressed enter. And I got... Error 17 Not able to mount partition(I think)
So now i reinstalled Ubuntu and now I am afraid to install the updates. Do you know why or what happened that caused grub not to be able to mount the partition?

Xp and Vista worked just fine and Ubuntu is working again but right now I am not going to install the updates in fear that this will happen again.

---

### Post by bulldog on 2006-12-15
You can update safely and when you get this error again.don't panic :D 
There's nothing wrong with your ubuntu,just examine your menu.lst and see it it points to the right partition.

A reinstall is not needed in most cases.:D

---

### Post by natoodo on 2006-12-16
Ok, And how can I access menu.1st form the grub boot menu?

---

### Post by natoodo on 2006-12-16
Ok. I installed the updates and it works! So right now Ubuntu is up to date, but again how could i edit menu.1st in the grub? menu

---

### Post by bulldog on 2006-12-16
Its menu.lst not with a one but a lower case L.

To edit your menu.lst```
gksudo gedit /boot/grub/menu.lst
```
Make a safety copy first```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

Make a file with gedit and safe it to your Desktop.
Write all the important commands you'll see in this text file,for later reference.

To reconfigure your X-server,
```
sudo dpkg-reconfigure -phigh  xserver-xorg
```
To restart gdm,
```
sudo /etc/init.d/gdm start  {you can also use restart or stop}
```
To start X-server,
```
startx
```

---

### Post by natoodo on 2006-12-16
Ok. Thanks

---

