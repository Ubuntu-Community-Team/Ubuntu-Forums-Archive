---
title: "What kernal?"
date: 2005-11-19
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2005-11-19
I need to know what kernal number I have in order to obtain a linux driver for my modem. I have ubuntu 5.10

---

### Post by adwait on 2005-11-19
```
uname -a
```

The part which says something like 2.6* is the kernel version.

---

### Post by amwil1024 on 2005-11-19
I'm new to linux and not a programmer. Where do I enter the command you specified?

---

### Post by mgor on 2005-11-19
open up gnome-terminal (alt+f2, and enter gnome-terminal) or if you're using kde, konsole.
then run the uname program.
```
micke@zaphod:~$ uname -r
2.6.12-9-686
micke@zaphod:~$ uname -a
Linux zaphod 2.6.12-9-686 #1 Mon Oct 10 13:25:32 BST 2005 i686 GNU/Linux
```

'man uname' to see what other flags it accept.

---

### Post by adwait on 2005-11-19
Dude......read my signature! The terminal is somewhere in your GNOME menu.....dunno where exactly coz I am not using gnome, but somewhere in Menu>System or something like that.

---

### Post by amwil1024 on 2005-11-20
Found kernal!
Thanks All!

---

