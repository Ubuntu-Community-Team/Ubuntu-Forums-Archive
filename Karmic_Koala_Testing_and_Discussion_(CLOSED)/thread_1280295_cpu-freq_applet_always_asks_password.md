---
title: "cpu-freq applet always asks password"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by monraaf on 2009-10-01
Hi, I just updated from Jaunty to Karmic but now the CPU Frequency Scaling applet always asks for a password when I want to change the frequency. This is very very annoying, please how do I fix this.

---

### Post by Finalfantasykid on 2009-10-01
```
sudo dpkg-reconfigure gnome-applets
```

I don't have karmic (just Jaunty), but if you havn't tried that, it might fix you problem.

---

### Post by monraaf on 2009-10-01
Thanks for the reply. Thats indeed the way I also did it in Jaunty but it doesn't do anything in Karmic.

---

### Post by DerSkw on 2009-10-06
Same for me. I switch the governors very frequently so its really annoying me :(
What happened to the option to remember the legitimation? (it was possible in jaunty)

---

### Post by DerSkw on 2009-10-28
*bump*

---

### Post by sdm_cacto on 2009-10-28
*bump*

---

### Post by mc4man on 2009-10-28
see here posts 3 and 5

This is a temp workaround till they provide the means to set this

I have adjusted both the cpu applet and the mounting and un mounting of internal drives.

Note:
don't do crazy adjusting this or that or you may find unexpected behavior

( for instance I found a way to have all partitions auto mounted at boot with no fstab or auth. needed. - not what I was looking for but interesting nonetheless

Read the edits.

[http://ubuntuforums.org/showthread.php?t=1299820](http://ubuntuforums.org/showthread.php?t=1299820)

---

### Post by DerSkw on 2009-10-29
hey thanks!
At least we have a workaround until this got fixed

---

