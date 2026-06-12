---
title: "Help with Radeon 9250 128MB Graphics card"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by wolf187 on 2010-04-03
Hello everybody
 
I am quite new to Ubuntu and I am using Ubuntu 9.10- Karmic Koala. I am not sure if this is in the right topic. I have tried to install my graphics card which is a Radeon 9250 128MB but it has not worked I used the xorg xserver for the graphics card and it still does not work . Can anyone help me with how to install this graphics card I used the envy package and that also did not help, I tried searching around but nothing helps and I cannot run alot of games that require the 3D acceleration. I also installed the 3DRI package for my OS but it does not work and tells that there is not 3D graphics card installed, I also installed ATI Catalyst Control center and it still does not work for the graphics card. Your help is greatly appreciated.
 
Thanks
Yashin

---

### Post by Mark Phelps on 2010-04-03
There is no ATI Linux driver that will work with your card and current versions of Ubuntu.  Trying to force the install of an ATI driver using something like EnvyNG is only going to trash your display.

The link below has instructions for removing the ATI drivers:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Once the driver are removed, when you reboot, Ubuntu should install the open source drivers by default.

---

### Post by wolf187 on 2010-04-10
Can you also tell me which 3D games I will be able to play with this graphics card because games like Metal Blob Solid 2 and a few others are not working. Thanks in advance

---

