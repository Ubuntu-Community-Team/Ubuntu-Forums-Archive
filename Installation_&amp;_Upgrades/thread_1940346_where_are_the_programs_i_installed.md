---
title: "where are the programs i installed?"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by jekylhyde on 2012-03-13
Hi
where are the programs i installed?
they don't appear in the "start menu"...

---

### Post by Toz on 2012-03-13
Which programs did you install and how did you install them? If you installed them via the Software Centre from official ubuntu repositories, they should be listed there in their appropriate submenus.

---

### Post by jekylhyde on 2012-03-13
> **Toz said:**
> Which programs did you install and how did you install them? If you installed them via the Software Centre from official ubuntu repositories, they should be listed there in their appropriate submenus.

smplayer via Software Centre
its not in any sub menu

---

### Post by Toz on 2012-03-13
I just installed it and the menu item shows up in the Multimedia submenu. If you're still not seeing it, try opening a terminal window and typing in the following command to force a refresh of the menu:
```
xfdesktop --reload
```
...if that doesn't work:
```
killall -HUP xfdesktop
```
...if that doesn't work then log out and back in again.

And if that doesn't work, then there is another problem that will need some more investigation.

---

### Post by jekylhyde on 2012-03-13
> **Toz said:**
> I just installed it and the menu item shows up in the Multimedia submenu. If you're still not seeing it, try opening a terminal window and typing in the following command to force a refresh of the menu:
```
xfdesktop --reload
```
...if that doesn't work:
```
killall -HUP xfdesktop
```
...if that doesn't work then log out and back in again.

And if that doesn't work, then there is another problem that will need some more investigation.

the 1st command didn't help
what the 2nd do?
thanks

---

### Post by Toz on 2012-03-13
Sorry, should of explained better. The second command sends the HUP signal to the xfdesktop process and forces it to re-initialize itself. During the reinitialization, it will re-create the menu structure.

Have you edited the default menu structure in any way? 

Is this a straight xubuntu install or did you install xfce/xubuntu-desktop onto of another flavour of ubuntu?

---

### Post by jekylhyde on 2012-03-13
> **Toz said:**
> Sorry, should of explained better. The second command sends the HUP signal to the xfdesktop process and forces it to re-initialize itself. During the reinitialization, it will re-create the menu structure.

Have you edited the default menu structure in any way? 

Is this a straight xubuntu install or did you install xfce/xubuntu-desktop onto of another flavour of ubuntu?

the 1st just refresh
the 2nd re-create?


i ran the 2nd...no change

i have it on a usb stick

---

### Post by jerrrys on 2012-03-13
try opening it in terminal, enter

smplayer

---

### Post by jekylhyde on 2012-03-13
> **jerrrys said:**
> try opening it in terminal, enter

smplayer

it loaded
```
ubuntu@ubuntu:~$ smplayer
QGtkStyle was unable to detect the current GTK+ theme.
This is SMPlayer v. 0.6.9 (SVN r3447) running on Linux

```

i installed another app - & can't see it
so - it install them
but i can't see them:confused:

---

### Post by Toz on 2012-03-13
Have you logged out and back in again?

Can you post back the results of the following commands:
```

ls -l ~/.config/menus
ps -ef | grep xf
cat /usr/share/applications/smplayer.desktop
```

---

### Post by jekylhyde on 2012-03-13
> **Toz said:**
> Have you logged out and back in again?

Can you post back the results of the following commands:
```

ls -l ~/.config/menus
ps -ef | grep xf
cat /usr/share/applications/smplayer.desktop
```

i had to restart
strange that it didn't updated right after install :)
thanks

---

