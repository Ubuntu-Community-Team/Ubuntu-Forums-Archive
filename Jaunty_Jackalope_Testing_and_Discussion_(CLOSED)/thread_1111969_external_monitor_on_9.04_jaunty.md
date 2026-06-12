---
title: "external monitor on 9.04 jaunty"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by orixilus on 2009-03-31
Hi,
I just gave ubuntu 9.04 LiveCD a try to check if I could use an external monitor on my Acer1692WLMi and I can confirm it works (it doesn't in my 7.10 installation).

The problem is, I can't change the external monitor's resolution to the correct one. On system>preferences>displays I can choose from several resolutions, but none is the correct one.

how can I fix this? thanks

---

### Post by sindrejh on 2009-04-14
Try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It fixed a similar problem for me.

---

### Post by paradigm2 on 2009-04-14
Hmmm.  I have a related question (now that this one has seemingly been answered) which goes under this subject as well.

I also have an acer laptop connected to an external monitor.  The built in LCD screen on the laptop is extremely damaged and is all garbled.  The external monitor works fine however the laptop screen stays on.

Usually Fn+F5 or Fn+F6 would disable it.  Fn+F6 will disable the LCD and leave the external on, but as soon as I use the mouse or hit a key, the LCD comes back.

How can I permanentl disable the LCD but leave the external on?

---

