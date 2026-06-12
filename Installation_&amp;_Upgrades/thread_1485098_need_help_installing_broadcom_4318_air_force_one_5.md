---
title: "need help installing broadcom 4318 air force one 54g wireless card"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by mistichu on 2010-05-16
I have had trouble in nearly every linux distrobution cept for backtrack 3(heavily modified ubuntu 8) which has a lot of wireless drivers on it. i know A LOT of people in the past have had trouble with these cards. any help or ideas :) ?

---

### Post by mistichu on 2010-05-16
to be more specific i need to install it offline i dont have any online capabilities with ubuntu (im dual booting with windows)

---

### Post by mistichu on 2010-05-16
any suggestions ? i hate to use ndiswrapper for the simple fact i cant get he inf file
and the b43-fwcutter requires and internet connection

---

### Post by mistichu on 2010-05-16
bump

---

### Post by mistichu on 2010-05-16
any help what so ever at all?

---

### Post by mistichu on 2010-05-16
donald trump

---

### Post by PabloTempe on 2010-05-16
I believe this thread will help:
 
[http://ubuntuforums.org/showthread.php?t=1266620&highlight=cutter](http://ubuntuforums.org/showthread.php?t=1266620&highlight=cutter)
 
You need to install the b43 driver, I believe

---

### Post by PabloTempe on 2010-05-16
Actually, you should be able to go in the package manager, and install the latest driver that comes up. I think they may have updated the driver for 10.04, but I'm not sure.
 
I'm de-grading back to 9.10, and loading the "b43cutter" driver for my laptop.

---

### Post by PabloTempe on 2010-05-16
...sorry, b43-fwcutter. I believe this is a program which extracts the id info of your Broadcom 43XX wireless device, and then loads the appropriate driver.

---

### Post by mistichu on 2010-05-16
thanks bro that helped alot was looking forever on how to do it
btw i got the links to the actual firmware thats used in cojunction with b43-fwcutter

 [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
 [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

then 
b43-fwcutter --help and itll show you examples
going to back that up
i want to completely shut myself out and away from windows as much as possible :)

thank you  pablo im posting on it as i speak:guitar:

---

