---
title: "Add new HDD"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by JavaNut13 on 2009-12-03
I had 1 drive, it has Ubuntu 9.10 installed onto it. I have added another hard-drive to my computer, and is currently mounted at '/media/Seagate', and in true Ubuntu fashion, appears on the desktop.

How do I set it to mount so Ubuntu can use it as my system/ home folders, so when one harddrive is full, it will automatically spill my home folder onto the other disk.

---

### Post by stefanus6667 on 2009-12-03
Terminal

sudo mkdir /home/folder
sudo mount /dev/sda1 -o loop /home/folder

---

### Post by JavaNut13 on 2009-12-03
would this erase my current home folder if i did the following command:
sudo mount /dev/sdb1 -o loop /home/me
?

---

### Post by stefanus6667 on 2009-12-03
That was my mistake. But I down know what is your hdd adress.
if sdb1 that correct what you wrote

---

### Post by JavaNut13 on 2009-12-03
but how do I make so /dev/sdb1 will always mount to /home/me
set a script to do it at startup?

---

### Post by Grenage on 2009-12-03
You will need to create an entry in fstab.  In a terminal:

```
blkid
```

Make a note of your new drive's UUID, then edit /etc/fstab to include it.  I would write down full instructions, but a quick google for "ubuntu fstab" will give you all you need.

To check your fstab without rebooting:

```
sudo mount -a
```

---

