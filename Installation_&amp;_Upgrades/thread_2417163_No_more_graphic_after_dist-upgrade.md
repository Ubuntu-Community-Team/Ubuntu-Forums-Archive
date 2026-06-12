---
title: "No more graphic after dist-upgrade"
date: 2019-04-21
forum: Installation &amp; Upgrades
---

### Post by rob141 on 2019-04-21
Hello every one. Once again i really need your help please. Today i have done a dist-upgrade from version 16.10 to 18.04 and now unfortunatelly, i have no more graphic interface. All i have at boot is a command prompt.

I have a laptop with an inboard radeon 5600 HD series graphic card. 

i dont think the fglrx driver works anymore in this version somehow if that is the case. 

i dont know how to manually downlaod the later ATI driver with command prompt if necessary. 

i have added 3 files that i hope will help you help me please.

Thank you very much ;)

---

### Post by mörgæs on 2019-04-22
Correct, fgl-rx is a thing of the past. AMD has put a lot of work into providing good open-source drivers in stead.

If you decide to do a clean install of 18.04.2 (not saying it's your only option) then chances are good that all necessary drivers are installed automatically in the process and you don't need manual modifications.

---

### Post by rob141 on 2019-04-22
Thank your very much but i already have upgraded to 18.04 and it is why i have no more X window. 

When i boot, i can login but i am only on command prompt. 

If i do startx, all i have is the mouse pointer with an empty blue screen.

How do i get my X window back ?

---

### Post by rob141 on 2019-04-22
i solved the problem after i have enter this command:  [COLOR=#242729][FONT=Consolas]sudo apt install ubuntu-desktop --no-install-recommends[/FONT][/COLOR]

---

