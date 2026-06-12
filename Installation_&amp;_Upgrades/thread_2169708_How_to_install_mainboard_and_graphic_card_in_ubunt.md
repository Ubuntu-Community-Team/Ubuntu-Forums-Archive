---
title: "How to install mainboard and graphic card in ubuntu 12.10"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by babakflame on 2013-08-23
Dear Buddies

  I have a P8Z77-V Pro Motherboard and nvidia GEFORCE GT 610 graphic card. Both of these have installation CD for windows systems. I have installed ubuntu 12.10 on my system. How can I install these on ubuntu?  I mean what are the deirectives to write in teminal to become confident that my motherboard and graphic card work properly?
Additionally when my ubuntu starts up, there is a short graphic crash. I think by installing my graphic card properly, It should be removed.

  Regards
    Bobi

---

### Post by Mark Phelps on 2013-08-23
Basically, you don't.  Linux is not like Windows, where you follow an install with updating drivers.  The correct drivers are installed as part of the initial setup.

If you look under Additional Drivers, and a restricted Nvidia driver is available for your graphics card, it will offer you the option to install it.  Otherwise, the drivers already installed are what's available.

---

### Post by babakflame on 2013-08-23
Thanks mark for your hints. How about my graphic crash at the start of ubuntu ( a crashed page appear for some seconds and then disappear)?

  Bobi

---

### Post by Mark Phelps on 2013-08-23
If you're able to get to a desktop, then open a terminal, enter "lspci" and look for the line containing "VGA". That will list out the make and model video chipset you're using.  Post that information back here.

IF you can't get to a desktop, then try booting from an Ubuntu LiveDVD/LiveUSB and try to do the same thing.

---

### Post by babakflame on 2013-08-24
Hi Mark

I am able to get to the desktop. the following is the output of "lspci"

```
01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)


```
      
     Bobi

---

### Post by babakflame on 2013-08-25
Hi buddies   

Would somebodu plz hint me why do I experience a sudden crash at the start-up of ubuntu?
 I have still access to my ubuntu 12.10 distribution.      

     Regards      Bobi

---

### Post by eternal243 on 2013-08-25
Try reading this information on proprietary drivers. It might help you out if you change from the preinstalled drivers, although the small graphical error while loading ubuntu is nothing much to worry about, I got that too on one computer. =)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by babakflame on 2013-08-31
HI eternal 243

  I will look at your mentioned website. many thanks.
   Bobi

---

