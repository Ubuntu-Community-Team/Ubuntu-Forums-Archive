---
title: "Blank Screen"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by neoaddict on 2006-03-13
I'm trying to get the Ubuntu livecd to work, and it works for the most part, until it reaches the desktop.

When it reaches the desktop, the monitor goes into suspend mode and I can't do anything about it.

Any suggestions?

---

### Post by taurus on 2006-03-13
What kind of video card do you have?

---

### Post by neoaddict on 2006-03-13
[QUOTE=taurus]What kind of video card do you have?[/QUOTE]

I'm not sure because it was second-hand, but it's PCMIA (I think I typed it wrong).

---

### Post by pronuncer on 2006-03-13
I get exactly same problem in my machine. My video card is X800, anyone know what's wrong?

---

### Post by neoaddict on 2006-03-14
Oh my god!  I got it fixed.  :)

Once you reach the blank screen, press ALT+CTRL+F1, and you should end up in a terminal.  Type your password, then type in **sudo dpkg-reconfigure xserver-xorg** and set your display settings there.

I chose VGA for my monitor.  ^^

---

