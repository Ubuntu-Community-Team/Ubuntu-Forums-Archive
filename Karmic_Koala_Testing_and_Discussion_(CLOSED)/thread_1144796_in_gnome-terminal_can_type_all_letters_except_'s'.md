---
title: "in gnome-terminal can type all letters except 's'"
date: 2009-05-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by johnpason on 2009-05-01
I can't type letter 's' in gnome-terminal, but other letters I can type.
 In other places, such as firefox, gedit, I can type letter 's' correctly,what's my problem,why?

---

### Post by Kevbert on 2009-05-01
Maybe you've got a broken package and need to re-install gnome-terminal and gnome-terminal-data. You can get the deb file(s) from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/karmic/gnome-terminal").

---

### Post by Gina on 2009-05-01
> **johnpason said:**
> I can't type letter 's' in gnome-terminal, but other letters I can type.
 In other places, such as firefox, gedit, I can type letter 's' correctly,what's my problem,why?That's a weird one :(  I've been thinking about it but I can't think of anything - sorry :(

---

### Post by QwUo173Hy on 2009-09-21
I'm stumped too. Maybe go into Edit-> Keyboards Shortcuts and make sure the letter 's' hasn't been assigned to anything for that application. My 's' is working fine.

---

### Post by nanog on 2009-09-21
Possible explanation:

I've had keys spontaneously remapped as keyboard shortcuts in gnome-terminal (at least I think it was spontaneous). Check out edit ---> keyboard shortcuts and delete anything mapped to s.

---

### Post by som24 on 2009-09-21
really weird

---

### Post by knarf on 2009-09-21
I've had this as well on occasions, in many versions of gnome. I just close the terminals and open new ones, that usually works. You could try to reset the terminal (echo CTRL-v CTRL-o; stty sane - cut and paste that since you 's' does not work...) as that might work as well.

---

