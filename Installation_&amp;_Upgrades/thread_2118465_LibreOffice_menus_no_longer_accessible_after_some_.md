---
title: "LibreOffice menus no longer accessible after some time"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by Jenske on 2013-02-21
After a while (several minutes) I am no longer able to use the menus in LO. Nothing special was done by me, nor did any "interfering" process start or end to run when the menus are no longer accessible.
Oddly though, mouse gestures ARE still possible and SOMETIMES it is possible to access the menus via the mouse but NOT via the keyboard ... and vice versa.

If this happens, the only thing I can do is manually close LO using the close-button of the window and fully restart LO.

I'm using Ubuntu 12.10 and LibreOffice 3.6.2 (Dutch version).
I've already removed LO in Synaptic and reinstalled it, but without result.

What's wrong and how can I solve this annoying problem.

---

### Post by dino99 on 2013-02-21
Are you using gnome ? how are you logged ? (unity/gnome-classic/...)
what show .xsession-errors & /var/log/ ?

---

### Post by Jenske on 2013-02-22
I use Gnome ... but ...

I've discovered in the meanwhile that there was (or still is?) something wrong with gnome.

It started when I first discovered that, though Writer, Calc, Impress and Base of LibreOffice were installed, LibreOffice itself wasn't installed seperately. Foolish enough and for an unclear reason, I then decided to install LibreOffice.

From then the problems started.

So after a while I decided to remove all components via synaptic, that mentioned the word "LibreOffice" and consequently re-installed LibreOffice.

But unfortunately from then on the problems persisted.

First I noticed that on login in, there was no longer the choice to switch to Gnome, Classic Ubuntu or whatever. At first I didn't pay attention to this as I thought the problems had only to do with LibreOffice.

Havind read your question, I looked up in my installed software if Gnome was installed ... which wasn't the case.

So then I installed Gnome. From then on I did have the choice at login to start in Ubuntu, Gnome etc.

I must say that I remember a similar problem -- the unity-bar once disappeared after having made some changes -- that also had something to do with a "conflict" between Unity and Gnome.

That's it for now.

I now will check if LibreOffice still has the same problems.

I'll inform you as soon as I have some more information on this.

---

### Post by dino99 on 2013-02-22
you seems have made lot of tweaks on that system, like metapackage removed, ppa added maybe, ...

so check that ubuntu-desktop is installed, and reinstall it in case its already installed.

---

### Post by Jenske on 2013-02-23
It indeed seems something went wrong with the tweaks. I must say, though, that I didn't really make many tweaks, but I think that at a certain stage I may have deleted too much when trying to reinstall LibreOffice.

So until now, it seems that reinstalling ubuntu desktop did the trick.

---

