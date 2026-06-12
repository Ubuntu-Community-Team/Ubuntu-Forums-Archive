---
title: "xserver and fonts"
date: 2004-11-08
forum: Installation &amp; Upgrades
---

### Post by wilhelm on 2004-11-08
hey, i just got ubuntu installed. when i try to start the xserver with startx, ihte screen goes blank for a sec and then back to the cmdline.
when i look at the logs it says the the defoma fonts has changed , and it suggests some changes, though when i look at the files the changes are already there. but xserver just dun start.

any ideas

---

### Post by Dennis_k on 2004-11-08
have you tried to reconfigure your X server?

Sudo dpkg-reconfigure xserver-xfree86

---

### Post by Jos Walrave on 2004-11-08
Check whether or not gdm and xfree86 is installed.

Sequentially:

[FONT=Courier New][COLOR=DarkSlateBlue]$ apt-get update
$ apt-get install xserver-xfree86
$ apt-get install xserver-common
$ apt-get install xfonts-base
$ apt-get install gdm[/COLOR][/FONT]

If it appears that all this software is already installed, check your configuration settings with [FONT=Courier New]$ dpkg-reconfigure xserver-xfree86[/FONT].

---

### Post by wilhelm on 2004-11-08
ty guys i will give it a try and let u know...

---

### Post by wilhelm on 2004-11-08
ok i tried that but it didint quite work, well i noticed that i have many packages not installed. so i went for the reinstall, and i didn't make the same mistake as before, i skipped that connect to the internet thing, coz that keep me out of  work for 2 hours this morning  :mrgreen:  so i just let it finish and then it said that it didn't install a lot of packages due to sum errors. so go into aptitude and check the pkgs that must be installed (47) which of most is just for gnome and xserver.

the main problem seems to be libgtk2.0-0 that needs to be installed for most on the other pkgs to be installed. i was thing to apt-get install libgtk2.0-0 and check where that gets me.   any other ideas ?

---

### Post by wilhelm on 2004-11-08
i just tried that apt-get , but it also gave me errors, anyone know where i can download this libgtk2.0-0 and install it ?

---

