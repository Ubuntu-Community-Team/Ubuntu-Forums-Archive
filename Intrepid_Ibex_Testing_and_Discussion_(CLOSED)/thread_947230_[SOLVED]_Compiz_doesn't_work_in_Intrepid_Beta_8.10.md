---
title: "[SOLVED] Compiz doesn't work in Intrepid Beta 8.10"
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by the8thstar on 2008-10-14
Hey guys,

I was wondering if you ran into the same problem as me: I can't get Compiz to work anymore in Intrepid Beta. I wanted to know if this is a widespread problem or just me and my config here.

For the record, I plugged in a second monitor just to see what an extended desktop would be like and my problems really started after I unplugged it. Now I'm stuck with Metacity. Turning on the compositing option in gconf-editor doesn't solve the problem. Could my xorg-conf be messed up?

Thanks in advance for your help.

---

### Post by the8thstar on 2008-10-14
What an idiot I am.

Of course it was xorg.conf.

Anyway, for future reference, here is how I solved the problem:
> 
sudo gedit /etc/X11/xorg.conf

and

> sudo gedit /etc/X11/xorg.confZZZZZZ (old one with date and time)

I copied the contents from the latter into the former, saved, pushed CTRL + ALT + BACKSPACE and voila! Compiz and AWN are back!!!! Muahahahaha! :)

---

### Post by Reb on 2008-10-28
Do you recall how they differed?

---

