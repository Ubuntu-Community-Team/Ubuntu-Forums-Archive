---
title: "i cant login after upgrade (kubuntu)"
date: 2008-12-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kabotage on 2008-12-06
From 8.10 to 9.04, I am having problem logging in. It just keeps me back to login screen every time i login. and if i choose either failsafe or kde, it loads too slow and i only see my wallpaper on desktop. i have to choose recovery mode so i can login on console. how do i look for errors?

---

### Post by mickbuntu on 2008-12-07
I don't know a full answer to that question. Since noone yet replied to your question. I'll start off my saying all what happens is in: /var/log. You may want to check the syslog / kernel log boot log first. Also from console you may want to type dmesg to get last post boot information. Basically  /var/log and nano if you can't get gedit / kwrite / kate / "your favorite editor" to work. Vi if you know how to get around it. But Nano is a nice and easy out of the box editor.  Also 9.10 is a war zone. It is still not finished it may look better during later alphas.

> **kabotage said:**
> From 8.10 to 9.04, I am having problem logging in. It just keeps me back to login screen every time i login. and if i choose either failsafe or kde, it loads too slow and i only see my wallpaper on desktop. i have to choose recovery mode so i can login on console. how do i look for errors?

---

### Post by ShirishAg75 on 2008-12-07
hi kabotage, while what mickbuntu says is right, what I would also like to know what graphic card or integrated graphics chipset you have. If you have Intel integrated then you may have been also hit with bug [lpbug] 304871 [/lpbug] or one of the variants of the same.

---

### Post by kabotage on 2008-12-10
thanks for the reply. im using NVIDIA 5500 before then change to ATI R9550 and it still kicks me back to login page. ive install kubuntu 8.10 on my spare drive so i can access it with a graphical interface and seen a bunch of kern, syslogs and i open dmesg but i dont have any idea which or what are the errors to look for.

---

