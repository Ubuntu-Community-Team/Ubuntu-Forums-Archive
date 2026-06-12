---
title: "Ubuntu  15.04 LiveUSB or LiveCD ask for username and password."
date: 2015-05-03
forum: Installation &amp; Upgrades
---

### Post by banutito on 2015-05-03
This is happen on Toshiba Satellite L650 only with Ubuntu 15.04. Smae USBs and DVDs works on other computers fine
Kubuntu 15,04 and old releases of ubunbtu works fine on Toshiba L650.

Result of** lspci -nnk | grep VGA -A1**
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M] [1002:68c1]
        Subsystem: Toshiba America Info Systems Mobility Radeon HD 5650 [1179:fd12]



Also If I try to install 15.04 it installing succefuly, but stuks on loop of lighdm that ask for user password, if I put Password, the display blink, and after that it show login screen again.
also I tryed to install gdm, same loop.
In tty1 I can login without problems

result of lshw: [XML]("https://drive.google.com/file/d/0B1jUHI3wZkcQNHBOdndxejk1ajg/view?usp=sharing"), [HTML]("https://drive.google.com/open?id=0B1jUHI3wZkcQaUNHTzB6U2RvZG8&authuser=0")

---

### Post by banutito on 2015-05-03
Even an sugestion to debug?

---

### Post by bapoumba on 2015-05-03
Maybe this ? [https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/1445206](https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/1445206)
Where and when did you dl the iso ?

---

### Post by jerryh8391 on 2015-06-14
I don't know if this helps, but it just happened to me. I downloaded the x64 iso and put it on a usb stick. to test it I booted it on the PC I created it with. It asked for a user name and password. The PC in question is a 32 bit netbook. I took the same usb stick to my 64 bit laptop and it works no problems.

---

### Post by sammiev on 2015-06-14
> **jerryh8391 said:**
> I don't know if this helps, but it just happened to me. I downloaded the x64 iso and put it on a usb stick. to test it I booted it on the PC I created it with. It asked for a user name and password. The PC in question is a 32 bit netbook. I took the same usb stick to my 64 bit laptop and it works no problems.

Hi jerry and welcome,

You should start your own thread if you are having problems.

I would not load x64 iso on a 32 bit netbook, you should select the correct iso for your netbook.

---

