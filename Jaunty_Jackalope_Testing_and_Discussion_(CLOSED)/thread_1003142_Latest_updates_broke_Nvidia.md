---
title: "Latest updates broke Nvidia"
date: 2008-12-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by defconoii on 2008-12-05
These latest updates broke nvidia for my fx 5500
Commit Log for Fri Dec  5 17:34:43 2008


Upgraded the following packages:
iso-codes (3.4-1) to 3.5-1
libffi5 (3.0.7-1) to 3.0.7-1ubuntu1
libspectre1 (0.2.0.ds-1build3) to 0.2.2.ds-1
liburi-perl (1.35.dfsg.1-1) to 1.37+dfsg-1ubuntu1
linux-generic (2.6.27.10.13) to 2.6.28.2.2
linux-headers-generic (2.6.27.10.13) to 2.6.28.2.2
linux-image-generic (2.6.27.10.13) to 2.6.28.2.2
linux-restricted-modules-common (2.6.27-10.14) to 2.6.28-2.1
linux-restricted-modules-generic (2.6.27.10.13) to 2.6.28.2.2
pidgin-facebookchat (1.39) to 1.39-1
ttf-liberation (1.04.92.dfsg-3) to 1.04.92.dfsg-4
wpasupplicant (0.6.4-2) to 0.6.4-3
xserver-xorg-video-intel (2:2.5.1-1ubuntu4) to 2:2.5.1-1ubuntu5

Installed the following packages:
libdrm-intel1 (2.4.1-0ubuntu7)
linux-headers-2.6.28-2 (2.6.28-2.3)
linux-headers-2.6.28-2-generic (2.6.28-2.3)
linux-image-2.6.28-2-generic (2.6.28-2.3)
linux-restricted-modules-2.6.28-2-generic (2.6.28-2.1)

---

### Post by ronacc on 2008-12-05
can you tell what driver it is trying to use ? I don't believe the latest 180.11 supports the 5...fx series  according to nvidia you need 173.14 .

---

### Post by ronacc on 2008-12-05
can you tell what driver it is trying to use ? I don't believe the latest 180.11 supports the 5...fx series  according to nvidia you need 173.14 .

oops sorry for the double post

---

### Post by poutsinou on 2008-12-06
The 173.14.12 nvidia fails to compile with kernel 2.6.28. 
The last version [173.14.15]("http://www.nvnews.net/vbulletin/showthread.php?t=122423") resolved this issue :)

---

### Post by defconoii on 2008-12-06
"The last version 173.14.15 resolved this issue" 
Is this in the repos?  How did u install it, with the nvidia binary?

---

### Post by defconoii on 2008-12-06
When will this be added/updated?

---

### Post by poutsinou on 2008-12-06
It's still not in the repositories. I installed it by using the binary.

---

### Post by NeoFax on 2008-12-10
This driver has been out since November.  When can we expect to have this available?

---

### Post by Kow on 2008-12-10
Try using dkms this should ensure the nvidia module gets rebuilt during each kernel upgrade. I think you may need to reinstall the nvidia package after installing dkms in order for dkms to latch unto it. I should mention that dkms+virtualbox guest additions is currently broken. It builds the vbox modules incorrectly.

---

### Post by NeoFax on 2008-12-11
DKMS for the 173 NVIDIA drivers does not work currently as the 173.14.12 drivers do not build on a 2.6.28 kernel.  However, the .15 drivers do.  As stated previously you can use the NVIDIA download drivers and it works fine, but I prefer using the DKMS drivers just in case I decide to upgrade to a different video card manufacturer (ease of removing stuff).

---

