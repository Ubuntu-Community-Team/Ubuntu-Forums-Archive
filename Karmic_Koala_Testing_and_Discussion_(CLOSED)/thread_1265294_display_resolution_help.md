---
title: "display resolution help"
date: 2009-09-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2009-09-13
after some of the new updates i can only access ubuntu by using the 9.04 live cd. if i try to start normally i get the error message that i should have a screen resolution of 1440 x 900 -60hz. lost on how to fix i tried going to display and changing the settings while to the above. any ideas?

---

### Post by rburkartjo on 2009-09-13
just realized that i have not turned off my computer in a few days and there has been a bunch of updates. this seems to be a grub issue because i can use text mode only without live cd. guesss i will have to wait until next update comnes out and just update from text mode unless anyone has any ideas. still on live cd

---

### Post by rburkartjo on 2009-09-13
that was not the problem either. he is where i am at when i start my computer without the live cd i get the grub menu than the boot logo, the screen goes black with only blinking curser in upper left hand section. able to run off live cd fine

---

### Post by Woody1987 on 2009-09-13
I have the same problem with the blinking cursor. Sometimes it boots up ok but most of the time i have to go into recovery mode and select resume at the menu, from there it boots to the desktop.

---

### Post by rburkartjo on 2009-09-13
tks woody did not think it was just me but i still cant get out of text mode unless boot with a live cd

---

### Post by Woody1987 on 2009-09-13
have you tried xfix from within recovery mode?

---

### Post by rburkartjo on 2009-09-14
woody no how would i do that,tks

---

### Post by rburkartjo on 2009-09-14
should the alpha 6 update due out the 17th fix this issue. note all updates thru today have been installed and same problems exists

---

### Post by VMC on 2009-09-14
> **rburkartjo said:**
> woody no how would i do that,tks

I think he means go to recovery mode (put "single" on end of kernel stanza). Reboot and from Recovery choose root. Then issue this: ```
Xorg -configure
```. You can then edit the output file, which is "xorg.config.new". 

To test it backup "/etc/X11/xorg.conf then move xorg.config.new to "/etc/X11/xorg.config" (leave off the "new")

---

