---
title: "Problem in complete installationof ubuntu 11.04 on system reboot with CD over window7"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by kevincmaker on 2011-12-24
recently, i downloaded ubuntu 11.04 and burnt it on a CD... I didnt want the windows 7 version that i already had installed in my PC and so, i inserted the cd, rebooted my system and started my installation.. i had no internet connection... so installation processes like partitioning failed, and so i just continued to finish my installation....

i was asked to reboot my system.. when i do, i have this complete black screen with a white blinking cursor for a looong time...

All i want to know is whether this is a problem in installation or i have to really wait for that much time during my first reboot..... If there is an installation problem, can someone pls point out me what to do ??


The main problem is that i dont have both windows 7 and ubuntu 11.10 now completely installed in my system...

thanks in advance!!

---

### Post by BC59 on 2011-12-24
Boot and press SHIFT key after the bios to get the grub menu.
Select the default ubuntu kernel, and instead of pressing enter press E to edit.
Go down until the line that starts with linux /boot and to the end of "quiet splash” change it to "quiet splash nomodeset”.

---

