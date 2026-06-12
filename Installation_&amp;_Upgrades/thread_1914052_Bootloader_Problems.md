---
title: "Bootloader Problems"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by PadiSka on 2012-01-23
If I have windows and ubuntu is there anyway I can use the Windows bootloader MBR instead of grub? 

I have installed ubuntu and it replaced my bootloader with grub, but I want to change back! Is this possible?

Please help! 
Thanks!!!!!

---

### Post by darkod on 2012-01-23
What is wrong about using grub2 as your bootloader?

Using windows bootloader to boot ubuntu is not easy because by default it can't locate linux OSs.

It's much better and easier solution to use grub2.

---

### Post by lordadi on 2012-01-23
If you reallllly are sure that ubuntu's grub2 won't cut it for you, you can look at EasyBCD.
 
KEEP IN MIND: when there's a grub2 update, you will not be able to use EasyBCD and will have to boot Windows via Grub (and then EasyBCD) to make EasyBCD the default again. This CAN cause problems, be careful.

---

### Post by PadiSka on 2012-01-24
Thanks for the help! 

The reason I suppose I dont like grub is due to being so used to MS-DOS style bootloaders.ha. I think I will just stick with Grub. 

Would the problems associated with EasyBCD and Grub updates be very serious? Like what could actually happen?


Thanks again!!!!

---

### Post by nipunshakya on 2012-01-27
EasyBCD: i have used that before, and similar to you, i wanted to use windows loader instead of grub.
For that i used EasyBCD. Its simple to add entry of ubuntu and get a windows bootloader.  But in my case, this happened:
1. I boot my machine.
2. I get grub loader at first.
3.a. Selecting ubuntu would boot ubuntu(no problem). 
3.b. but choosing windows on the grub would then load windows boot-loader and present me with choosing windows and ubuntu. Choosing windows would boot the system to windows(no errors) but then choosing ubuntu would again take me back to grub menu and the whole chainload process would come over again n again.

When updating grub with this chainloading, i usually used to find my machine to same states even after update and restart. When i used grub only, i finally got my machine working fit and fine. Hope you don't go out of grub and use it instead of windows bootloader. Goodluck.

Regards,WinuxUser

---

