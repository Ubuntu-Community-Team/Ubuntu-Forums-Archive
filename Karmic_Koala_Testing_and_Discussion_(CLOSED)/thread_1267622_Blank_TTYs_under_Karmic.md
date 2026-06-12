---
title: "Blank TTYs under Karmic"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Scienceman123 on 2009-09-15
Whenever I switch to any tty other than the standard 7, I receive a blank screen. I am able to type and login, but cannot see the effects of said input. Starting X on another tty will not show up either. Specs in signature.

---

### Post by Scienceman123 on 2009-09-17
With kernel 2.6.31-10-generic in recovery mode (the only currently reliable boot method), all they show now is a blinking underscore, with no interaction possible.

---

### Post by BwackNinja on 2009-09-17
I'd try to do a 'sudo modprobe fbcon' other than that, I dunno

---

### Post by Scienceman123 on 2009-09-18
Didn't seem to work. In addition, a normal boot results in striped garbage being displayed.

---

### Post by creatorlarryli on 2009-10-04
I have the same problem. Anyone has any idea how to solve this?
I have already tried to set vga=791 and it doesn't work.

---

### Post by Crushyerbones on 2009-10-04
I need assistance too :S

Update: [http://ubuntuforums.org/showthread.php?t=1282368&highlight=tty](http://ubuntuforums.org/showthread.php?t=1282368&highlight=tty)

---

