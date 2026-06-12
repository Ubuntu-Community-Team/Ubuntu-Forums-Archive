---
title: "curses package"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by gnostlos on 2010-07-03
Where can I find the curses (or ncurses) package? "Sudo apt-get install" cannot find it, but surely it exists.

---

### Post by SmokeyThePanda on 2010-07-03
Hm. I have no idea what this package is or what it does, but after a quick google search, I found the below page. I hope it can help you.

[http://ubuntuforums.org/showthread.php?t=296224](http://ubuntuforums.org/showthread.php?t=296224)

---

### Post by hopeless8009 on 2010-07-03
are you talking about the network manager for Terminal?

---

### Post by gnostlos on 2010-07-03
Gnostlos says, I still do not know how to find curses.  For those who wondered what it is, it is, or used to be, a well-known library for controlling a terminal window.  A terminal window is a text window, of course, and curses has numerous ways of breaking the window into subwindows or putting pieces of text into different places on the window.  The name "curses" probably derives from its ability to control the cursor in the window.

---

### Post by wojox on 2010-07-03
Try:

```
sudo apt-get install libncurses5-dev
```

If that don't work open Synaptic and search for it. ;)

---

### Post by gnostlos on 2010-07-04
Wojox, Thank you.  libncurses5-dev installed immediately and compiled into my little program.  I'll have to learn to search for things with synaptics.

---

