---
title: "Entering runlevel 2"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by scorpio2002 on 2005-07-21
Hi there! I was trying to compile a kernel myself but I didn't manage to do it so I returned to the old kernel provided with Ubuntu.
But something strange happens. Now it enters runlevel 2. why is it so? I don't remember it having even entered runlevel 2 before. What's going on?

it says:

Setting up ICE socket directory [OK]
Enterin runlevel 2 [OK]

could it be that i has always entered runlevel 2 without me even noting it? I'm confused :|

---

### Post by uniko on 2005-07-21
Default runlevel should 5. You can read more [here](http://www.help2go.com/article164.html) . It's an article about linux runlevels, not too technical but nicely explanatory.

---

### Post by scorpio2002 on 2005-07-21
Well, that article is interesting but doesn't answer my qeustion: what's going on? I even starts the Gnome and everything seems to work just fine. How can I fix this?

---

### Post by Rodrigo on 2005-07-21
Ubuntu uses run level 2 to function
this is the default run level (in ubuntu).

Dont worry, it works as good as run level 5.
Its not necesary to "fix it".

I have all my Pc's with the same configuration.

---

### Post by musicman2059 on 2005-07-21
[QUOTE=Rodrigo]Ubuntu uses run level 2 to function
this is the default run level (in ubuntu).

Dont worry, it works as good as run level 5.
Its not necesary to "fix it".

I have all my Pc's with the same configuration.[/QUOTE]
 Ubuntu starts up in runlevel2, but after starting the xserver and such it normally switches automatically to runlevel 5.

Just for refrence:

0 = halt
1 = maitenance mode
2 = terminal single-user
5 = X multi-user
6 = restart

Yes, I know there's a 3 and 4, I just forget which one is terminal multi-user and X single-user.

---

### Post by Mr Frosti on 2005-07-21
Different run levels can be customized to start certain applications on boot-up, The "default" run level for Ubuntu, and Debian for that matter is 2. 

You can view the startup processes in the run level 2 by typing in ```
ls /etc/rc2.d/
``` 

This directory contains links to applications in your "/etc/init.d/" directory. There are 6 run levels, and you can enter any of them at any time by running "init #" where # is the run level you wish to enter. 

Entering run level 2 is what the machine normally does, and it isn't a problem.

---

