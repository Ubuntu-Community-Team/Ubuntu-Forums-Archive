---
title: "Nvidia 7600gs issue"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by ANDark on 2010-12-31
Hy to all firstly and a happy new year.


             Ill keep it simple: after installing ubuntu and graphic card drives(nvidia 7600GS) the enviroment looks very funny, colorfull and stuff.. like a 4bit color range. 
          It started looking like this about a week ago(up to date Ubuntu and Drives) so i decided ti try and install windows XP. Done that, all started as normal with low resolution and 4bit colours; but after installing the drives, instead of nice looking details i get the "No signal" message from my monitor each time i try to boot the OS. 
            Now i have ubuntu installed but with no graphic card drives. If i install them it gets wild again and if I keep it like this i have a great amount of issues in watching a film, using a render or so..

Any ideas of what's wrong.....i suppose it's the graphic card itself

---

### Post by dino99 on 2010-12-31
welcome,

which ubuntu release are you talking about ? is it a fresh install ?

remove xorg.conf:

sudo rm /etc/X11/xorg.conf

then reboot

---

### Post by ANDark on 2011-01-01
all of them...i installed 9.04 upgraded to 9.10 and 10.04 but nothing changed, problem still there. I'll try the command suplied by you when i get home and reply after.

---

### Post by takemylife on 2011-01-01
i have the same problem
nvidia 7100 :/ 
any help? :P

---

### Post by ANDark on 2011-01-07
Sorry for the long delay, i was on a trip. I did the command to remove xorg.conf and it seems it removed my graphic card drivers because the image has an offset to the right and i can't use programs or games that require 3D acceleration. Also the image looks normal now.

---

