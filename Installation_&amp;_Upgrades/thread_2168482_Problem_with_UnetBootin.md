---
title: "Problem with UnetBootin?"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by Andrew_Kahn on 2013-08-18
I recently downloaded the 13.04 version of Ubuntu ([SIZE=3]and I am loving it.[/SIZE]) but there is one problem whenever I boot it all my previous files from the last boot disappear. I have a semi old computer that can't even run Windows XP (It will just crash) I have blank DVDS but my optical drive has been acting up. Thanks for the help.[FONT=comic sans ms][/FONT][FONT=comic sans ms][/FONT]

---

### Post by coldraven on 2013-08-18
If I understand correctly you have created a bootable USB key using Unetbootin.
You have not installed Ubuntu to the hard drive but are using in Live mode from the key.
If that is correct you would need to make a USB key with persistence, that is it has a partition that keeps your files between boots.
You would need another USB key with enough space for your files. With a 1 GB key you would get about 250MB of space, more with a larger key.
Boot with your existing key.
Plug in the spare one and find out it's address
```
sudo fdisk -l
```
Run "Startup Disk Creator", **select the correct USB key**, select the amount of persistence space and you should be good to go.

Edit: this would create a key to replace the one you have. You could just plug in an empty key and use it to store files on.

---

### Post by Andrew_Kahn on 2013-08-18
I am [SIZE=5]NOT [/SIZE]using a usb or blank dvd/cd I used unetbootin and it let me not use those.

---

### Post by Cheesemill on 2013-08-19
UNetBootin cannot be used to properly install Ubuntu onto a hard drive.

If you pointed UNetBootin to your hard drive then what you have done is created a Ubuntu installer out of your entire hard drive, you haven't actually installed Ubuntu. This is whay all of your settings and documents are lost every time you reboot, you are just running the Live version of Ubuntu just as if you were testing from a CD.

You need to create either a botable USB or DVD using the Ubuntu iso file you downloaded and then use that to install Ubuntu.

---

### Post by Lim_Xiang_Yann on 2013-08-19
If you have windows (tried on 2000,xp,7)
try open with the wubi.exe

---

