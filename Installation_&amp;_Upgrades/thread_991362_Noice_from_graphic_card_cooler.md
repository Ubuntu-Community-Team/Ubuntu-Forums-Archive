---
title: "Noice from graphic card cooler"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by raketten on 2008-11-23
I have noice from cooler in UBUNTU, but not in XP.
My system is:
Gigabyte GA-EG31M-S2
Intel Core 2 Duo E8400
2x2048 MB DDR II SDRAM PC2-6400
512MB GeF 9600GT TV-Out PCI-E/DVI + ASUS My Cinema P7131

Hope for help.
/raketten

---

### Post by Philio on 2008-11-23
Do you have Compiz enabled while on Ubuntu (3D accelerated desktop - It turns on automatically when you install the restricted driver)?

If so it could be that the GPU is being used more than XP's 2D desktop.

You could check the GPU temps and see if this gives more indication, e.g. if hotter in Ubuntu that is likely the reason.

Bit of a guess, as I don't have XP or an air cooled GPU but hope it helps :)

---

### Post by raketten on 2008-11-25
I should have mentioned, that i am new to ubuntu. Compix? Whats that?
But when i play 3D games in XP, the cooler is silent.

By the way: sysinfo says
Graphic Card
VGA compatible controller
nVidia Corporation Geforce 9600 GT 512 (rev a1) (prog-if 00 [VGA controller])
/raketten

---

### Post by raketten on 2008-11-25
Ther is no nVidia driver installed
Why is it so hard to install a graphic driver for nVidia???
I can see, that many other people have the same problem with fan noise from geforce in ubuntu.
It seem that Fan Mate 2 is the only solution!!

---

### Post by cariboo on 2008-11-25
It isn't hard to install any drivers in Linux, it is considerably easier then Windows. Go to System-->Administration-->Hardware Drivers and select the recommended driver and click activate. Wait for it to download, it may take several minutes and let the process finish. Then press Ctrl-Alt-Backspace and driver will work.

Jim

---

### Post by raketten on 2008-11-26
Ive have tryed, but even i can find the driver ubuntu wont let me install it. the option is grayed out. 

But now I will try installing the new ubuntu 8.10 to see if this is helping.

---

### Post by raketten on 2008-11-26
YES!
Ubunti 8.10 solved the problem!!!
I installed 8.10 and thereafter nVidia 177 and voila! No noise and 3D effects on desctop! Super!

---

