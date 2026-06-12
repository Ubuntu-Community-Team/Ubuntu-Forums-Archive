---
title: "i can not install ubuntu 9.10 from usb flash memory"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by mohmmed_eltaher on 2009-12-21
hi every body
i have big problem in my computer
i was use ubuntu 9.04 then i upgrade to ubuntu 9.10
now i have many problems in my OS so i have to reinstall ubuntu 9.10
i was download ubuntu 9.10 and becouse i have not cd\dvd i try to install it from usb flash memory
i am use many of program to boot from usb flash memory such as: unetboot, ubuntu live usb creator and the program that come with ubuntu usb setup disk creator
and whene i starting installing the language screen appeare then i choose  "install ubuntu" then i see black screen without and donn't go to anther step 
this problem appear also if i choose the 1st to open the live cd
what can i do????

---

### Post by presence1960 on 2009-12-21
> **mohmmed_eltaher said:**
> hi every body
i have big problem in my computer
i was use ubuntu 9.04 then i upgrade to ubuntu 9.10
now i have many problems in my OS so i have to reinstall ubuntu 9.10
i was download ubuntu 9.10 and becouse i have not cd\dvd i try to install it from usb flash memory
i am use many of program to boot from usb flash memory such as: unetboot, ubuntu live usb creator and the program that come with ubuntu usb setup disk creator
and whene i starting installing the language screen appeare then i choose  "install ubuntu" then i see black screen without and donn't go to anther step 
this problem appear also if i choose the 1st to open the live cd
what can i do????

Start at the beginning:

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso you downloaded prior to making a bootable CD/USB?
When you boot the USB did you choose "check disk for defects" prior to trying the Live CD or installing?

If the above does not correct the problem hit F4 at the menu and choose safe graphics mode. See [here]("https://help.ubuntu.com/community/BootOptions") for more info on boot options for the Live CD/USB.

If still having problems you may have to try the alternate text based installer from [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

