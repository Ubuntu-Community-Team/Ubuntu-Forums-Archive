---
title: "Installing Xubuntu on Ubuntu"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Klaidas on 2006-06-05
Hello :)
I have a very simple and quick question:
If I install Xubuntu (sudo aptitude install xubuntu-desktop), would I break my menus? I mean Xubuntu's applications appearing on GNOME and GNOME's apps appearing on Xubuntu?
If so, is there a way to prevent that?

What I'm trying to do is try out Xubuntu without downloading the large desktop iso :)

---

### Post by ubnoobie on 2006-06-05
the menus pull from the same data; so apps from both desktops will appear in each one's menus. but apps from one desktop will run fine on the other; so this isn't really a 'problem'.. in fact, you'll get added functionality and configuration options in xubuntu because of the ubuntu apps.

---

### Post by Klaidas on 2006-06-05
When I remove xubuntu, will all those applications be gone too? from my harddrive AND the menus? :)

---

### Post by nanotube on 2006-06-05
[QUOTE=Klaidas]When I remove xubuntu, will all those applications be gone too? from my harddrive AND the menus? :)[/QUOTE]
if you use aptitude, then yes, they should be.

---

### Post by Klaidas on 2006-06-05
Ok, thank you for answers :)

---

### Post by aysiu on 2006-06-05
Don't forget to do ```
sudo aptitude update
``` before you do ```
sudo aptitude install xubuntu-desktop
``` Otherwise, the dependencies won't be tracked when you remove it with aptitude.

---

