---
title: "X don't start"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rewz on 2009-08-25
Hi, After todays update x don't start, i tried to reconf. X but it did not help... I have an Nvidia card.

any suggestions?

/Mats

---

### Post by taavikko on 2009-08-25
Recovery-mode -> root shell with networking->
```
aptitude update && aptitude full-upgrade && aptitude install nvidia-185-kernel-source
```
check that the driver has been correctly build
```
dkms status
```

Edit xorg.conf and add 
```
Driver "nvidia"
```
Under Device section.

Exit the root shell command: exit
then start normally.

---

### Post by rewz on 2009-08-25
Thanks i the problem i solved i reinstalled the Nvidia driver...

---

### Post by Regenweald on 2009-08-25
If you are using the Nvidia driver from their ftp site, with every Kernel update you MUST rebuild the nvidia kernel module.

---

### Post by dinxter on 2009-08-25
nvidia 180 drivers should be dummy drivers that upgrade to 185 drivers, unfortunately due to a version conflict between nvidia-glx-180 and nvidia-glx-185, glx-185 isnt being installed on upgrade. end result is we have the kernel module but no X support
see 
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/418681](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/418681)

---

### Post by Regenweald on 2009-08-25
I noticed that 'safe-upgrade' was consistently holding them back.

---

