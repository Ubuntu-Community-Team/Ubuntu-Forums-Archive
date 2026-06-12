---
title: "No Desktop on Intrepid!"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andreselsuave on 2008-10-12
Hi there, I upgraded my 8.04 fully updated to ubuntu intrepid and got some errors with some packages during the process.

Now I can get to the users login screen but when I login in any of them, I get only the mouse pointer and nothing else loads. What happens? I didnt do a backup :S:S 

thanks in advance

---

### Post by Aikon- on 2008-10-15
The following worked for me.. try switching to a terminal (Ctrl-Alt-F1) or booting in single-user (recovery) mode, and then:

```
$ sudo apt-get install compiz-core
$ sudo reboot
```

---

### Post by Yoshiman007 on 2008-10-18
I picked a Gnome session in the options menu and made it default. This worked after *removing* compiz as other posters suggested. good luck

---

