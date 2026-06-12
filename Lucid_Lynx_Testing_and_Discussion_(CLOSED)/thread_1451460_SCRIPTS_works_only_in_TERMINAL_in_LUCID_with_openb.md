---
title: "SCRIPTS works only in TERMINAL in LUCID with openbox wm"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by azanutta on 2010-04-10
Hi!
i'm writing because i've got a problem in applying the crunch-scripts in my ubuntu lucid distro...
i've got of course openbox ;P and i'm trying to get an EXIT script to work, following this guide [http://crunchbanglinux.org/wiki/installing_scripts](http://crunchbanglinux.org/wiki/installing_scripts) .

downloaded the script file from official crunchbang site, chmodded, saved in the bin directory under my user, and finally, as described in the wiki, added the PATH to .bashrc ...

the result is that when i type the name of the script in a terminal, it works...
but...
when i select it in the OB menu OR when i type the name in gmrun (ALT+F2), it doesn't..

i've tried to add the PATH also to the .profile file, but the problem still remains...
checking to the EXIT menu entry with obmenu, turns out that it points truly to "openbox-logout"
so i'm wondering if the sistem can't bypass the /bin/ directory when i put only the name...
can anyone figure this out?
thanks!

---

### Post by azanutta on 2010-04-22
bump!

---

### Post by kerry_s on 2010-04-22
put the script in /usr/local/bin as root, it's the best place & you don't have to change a thing. you can even do overrides for commands by using the exact same name as in /usr/bin.

i run several on my openbox+lxde+xfce4 setup.

---

