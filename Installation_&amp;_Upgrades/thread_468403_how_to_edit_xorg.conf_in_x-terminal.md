---
title: "how to edit xorg.conf in x-terminal?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by amdfanboy on 2007-06-08
my system won't properly boot and can't go into GUI mode...i managed to pinpoint the problem...but i can't seem to edit xorg.conf in x-terminal mode...

tried using gedit but don't know what parameters to use...

it says

"no screens found"

what should i do?

---

### Post by 5-HT on 2007-06-08
You can use nano to edit the file (gedit requires X).
```
sudo nano -w /etc/X11/xorg.conf
```To save and exit: Ctrl+x
To restart X: ```
 sudo /etc/init.d/gdm restart
```*replace gdm with kdm, xdm if you are using them.

---

### Post by tbroderick on 2007-06-08
sudo nano -w /etc/X11/xorg.conf

or learn to use vim ;)

---

### Post by amdfanboy on 2007-06-08
done...thanks for the help ^_^

---

### Post by amdfanboy on 2007-06-08
one problem though...i tried the restart command (one with gdm,kdm,xdm)...i tried the 3 but nothing happened...

---

### Post by pt123 on 2007-06-08
You start X by 

startx

you can also try rebooting

what did you edit in the file?

---

### Post by amdfanboy on 2007-06-08
hmm, just a couple of typo-errors made when installing beryl ^_^

---

