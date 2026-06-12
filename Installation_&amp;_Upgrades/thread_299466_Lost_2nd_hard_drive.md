---
title: "Lost 2nd hard drive"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by SergioA on 2006-11-14
Hi there!

Just installed 6.10 overwriting the previous 6.06 installation: my PC has 2 hard drives, correctly seen in 6.06, now I can only see the 1st drive but if I open my "Computer" icon on desktop I can see two floppies... The correct one is labeled "Floppy Drive", then there is "Floppy 1" and "Properties" says 6.7 GB of free space (that's the free space of my decond HD!!!)

I succeded in mounting the 2nd HD with:

sudo mkdir /mnt/second
sudo muount -t ext3 /dev/hdd1 /mnt/second

and made a link to it on my desktop, but I seem to remember that in 6.06 things were easier and results were better...

Any idea?

Thanks and ciao

Sergio

---

### Post by taurus on 2006-11-14
You need to mount it to /media for it to appear on your desktop.  And if you want it to mount everytime you boot, then you need to add an entry in /etc/fstab so it would be mounted automatically each time you boot Ubuntu!  Open a terminal and type

```
gksudo gedit /etc/fstab
```
Now, add this line at the end of it.

```

/dev/hdd1   /media/second   ext3   defaults   0   1

```
Save it and run these commands.

```
sudo umount /mnt/second
sudo mkdir /media/second
sudo mount -a
df -h
```

---

### Post by SergioA on 2006-11-14
Hi Taurus,

it works! Thanks a lot ;-)

Sergio

---

### Post by taurus on 2006-11-14
You're welcome and have fun.

---

