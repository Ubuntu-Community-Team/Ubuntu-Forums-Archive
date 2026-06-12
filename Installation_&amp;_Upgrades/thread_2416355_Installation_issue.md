---
title: "Installation issue"
date: 2019-04-09
forum: Installation &amp; Upgrades
---

### Post by zhzau on 2019-04-09
Hi,

First of all please let me apologize for my worst english, but it's not my language. I'm a newbie, i've used ubuntu for a lot of time but with no problem so I can't do anything apart of using it. I'm trying to install lubuntu 18.10 (using an usb memory) on an old Hp G6 laptop (i5 3320m, 8 gb ram, Radeon Hd7670m) and after boot when i try to use trackpad the sistem crash and give me error uvd not responding. I've googled for it and find that there's a kind of incopatibility between radeon gpu and linux...cna you help me?
Please let me now if I've to give you any other information.

---

### Post by Autodave on 2019-04-09
First of all, I would stick with the long term releases.  18.04 was the last one.  20.04 will be the next one.  That garphics card should work just fine with the driver that comes with Lubuntu.  Try downloading the 18.04 release and boot to that and see if everything works.

---

### Post by zhzau on 2019-04-09
Thank you. I've used the 18.04 release and after installation I've had the same problem. This time installation was, I don't know the right name, like an 8bit gui so I've been able to add the "radeon.modeset=0" option to grub (before first run of os and than adding and saving with the shell). I'm testing the whole sistem just for some days and letting know if my problem is solved

---

