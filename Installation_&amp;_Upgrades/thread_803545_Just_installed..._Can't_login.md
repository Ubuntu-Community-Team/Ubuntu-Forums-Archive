---
title: "Just installed... Can't login"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by TaintedBllack on 2008-05-22
I just installed hardy and the installation seemed to work perfectly.. The only problem is that when I try to login it starts to load, I hear the login sound, then the screen goes black, and then it goes back to the login screen.

Any help would be greatly appreciated.

---

### Post by bigken on 2008-05-22
try this boot in safe mode 
at the promt type sudo apt-get update then sudo apt-get upgrade then sudo apt-get install ubuntu-desktop then startx

---

### Post by TaintedBllack on 2008-05-22
When I try startx I get the following error: 

Server is already active for display0

---

### Post by bigken on 2008-05-22
try a reboot

---

### Post by TaintedBllack on 2008-05-22
Just rebooted and having the exact same issue. :-(

---

### Post by bigken on 2008-05-22
ok dont panic at the prompt type sudo dpkg-reconfigure xserver xorg and select vesa as your driver this should at least get you too a desktop well sort the correct driver later

---

### Post by bigken on 2008-05-22
do you know your video card make model ?


sorry its 
sudo dpkg-reconfigure xserver-xorg

---

### Post by TaintedBllack on 2008-05-22
every time It comes to keyboard options I get the following:

xserver-xorg postint warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2008052213021

and I can't seem to get past this.

---

### Post by bigken on 2008-05-22
just hit enter or use the arrow keys to select next

---

### Post by TaintedBllack on 2008-05-22
> **bigken said:**
> just hit enter or use the arrow keys to select next

That is what I was doing.. When I hit enter at the keyboard options I get that error and it won't let me do anything else.

---

### Post by bigken on 2008-05-22
hmm this is a new one on me ok try this 
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by TaintedBllack on 2008-05-22
> **bigken said:**
> hmm this is a new one on me ok try this 
sudo dpkg-reconfigure -phigh xserver-xorg

When I enter that command it gives me the xserver-xorg postint warning again.

---

### Post by bigken on 2008-05-22
could be the space bar to select ? sorry but i realy dont know I cant even try it as im running kde

---

### Post by bigken on 2008-05-22
this might help [http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

---

### Post by TaintedBllack on 2008-05-22
As soon as I try to hit enter at keyboard options it gives me that error and It brings me back to the command prompt.

---

### Post by bigken on 2008-05-22
have you tried entering your keyboard region

---

### Post by TaintedBllack on 2008-05-22
> **bigken said:**
> have you tried entering your keyboard region

Yep.. have no problems with that.. It is the next part (keyboard options) where I get stuck.

---

### Post by bigken on 2008-05-22
> **bigken said:**
> try this boot in safe mode 
at the promt type sudo apt-get update then sudo apt-get upgrade then sudo apt-get install ubuntu-desktop then startx


when you did these commands were yyou in safe mode the second boot option in the grub menu

---

### Post by TaintedBllack on 2008-05-22
> **bigken said:**
> when you did these commands were yyou in safe mode the second boot option in the grub menu

Yes

---

