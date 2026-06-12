---
title: "Installing Server Ubuntu"
date: 2006-03-27
forum: Installation &amp; Upgrades
---

### Post by J.J Morrison on 2006-03-27
I tried doing the regular install what feels like a million times and it never worked so I decided to try the server installation will someone guide me through this.:confused: 


Pentium II 2.0 gigaherts
256 ram
2 gb harddrive(i think this is my problem):confused:

---

### Post by gazj on 2006-03-27
I think this is your problem, im sure the default install of ubuntu is over 2gb.  The server install is down to a few hundred MB, you can keep the install small by installing the fluxbox desktop instead of the normal ubuntu (gnome) desktop, but this is quite hard to setup, Fluxbox is a very lightweight and very fast window manager, and will be much better on a machine of that speed, i think you would probably fine the gnome desktop too slow.

There is also the xfce desktop which is easy to setup, but i don't know if this will overstep the 2gb limit, but to give it a try do a server install, log in, and then type

```
sudo apt-get install xubuntu-desktop
```

you need a connection to the net to do this though

---

### Post by gazj on 2006-03-27
i apologise didn't read the speed of your machine right, thought is said 200mhz at a glimpse, 2ghz and 256mb ram would be fine for gnome desktop, its just that hd

---

### Post by J.J Morrison on 2006-03-27
I can't even log in  so i doubt i will be able to do either of those.

---

### Post by gazj on 2006-03-27
I remember your previous thread, im really sorry you aren't having much luck, can you not even log-in with a server install?

---

### Post by J.J Morrison on 2006-03-28
No I still can't login. I am planning on buying a new hard drive for this computer so hopefully everything will work out.

---

