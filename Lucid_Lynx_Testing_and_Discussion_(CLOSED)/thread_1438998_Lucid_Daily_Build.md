---
title: "Lucid Daily Build"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zoomy942 on 2010-03-25
So I installed the daily build today.  it all went fine, and with the alpha, I put the CD in and installed the bcmwl-kernel-source would install and I was online easy.  with this beta/daily build, i do the same process and the bcmwl fails to install.  i get a 

bcmwl-kernel-source:subprocess installed post-installation script returned error exit status 6.


what am i missing?

---

### Post by Intrepid Ibex on 2010-03-26
> sudo aptitude -f install

If it does not work, then you may want to try:

> sudo dpkg --force all --remove

---

### Post by zoomy942 on 2010-03-26
turns out one of the packages it needed it was getting off the web.  once i plugged in my cell phone and got it online, it DL'd everything and worked.  i only didnt think of that because i have a vzw mifi - which has no plug in ethernet port.  all wireless only.

---

