---
title: "vboxnetflt fails with dkms"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xalaros on 2009-03-28
Hello,

maybe this isn't the place to post this since i had the same issue with intrepid as well but what the heck.
So i have virtualbox 2.1.4 installed and everytime i install a new kernel dkms fails to recompile vboxnetflt.ko both during the update process and during reboot.
As i said i had this problem in intrepid as well but in jaunty also.
When i use the sudo /etc/init.d/vboxdrv setup manually everything works great.
So probably this is a dkms problem, anybody else experiencing the same issue. I am running x64 ubuntu jaunty Beta. dkms version is: 2.0.21.1

---

### Post by toasterboy1 on 2009-03-31
Just noticed this as well. AMD64 system. Virtualbox has never run quite right since I started using Jaunty maybe because Virtualbox was not compiled for Jaunty as I use the Intrepid repo.

---

