---
title: "Hardly anything runs in intrepid after graphics update"
date: 2008-10-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dr_james2k on 2008-10-21
Hi guys, I've run into quite a bit of a problem. 

I upgrade to Intrepid yesterday and on logging in got a few messages about graphics problems.  After a bit of research I managed to fix them, get the latest nvidia kernal running and all that but as soon as I got that fixed a new problem popped up so I'm guessing they're related.

Now when I try to run something (almost anything) I get a bar on the panel saying that the application is starting for a couple of seconds then its gone.  This includes firefox, nauticus, the terminal and the update manager among many others.  Infact its easier to list the apps which still work: vlc, awn-window-navigator and the gnome games are the only things I've found so far which work.
(Rythmbox is present as a logo on start up and plays music through keyboard shortcuts but when I click it to open it, it crashes)

Has anyone had a similar experience or know of a solution?

Many thanks to whoever can help.

---

### Post by jerrylamos on 2008-10-21
When you boot up try System Preferences Appearance Visual effects None.  That turns off compiz (mostly).  Compiz does strange things with graphics hardware and drivers to get "eye candy".

Another method if it will boot and bring up a terminal is
metacity --replace &
which might get compiz off before it does any damage.

Jerry

---

### Post by dr_james2k on 2008-10-22
Thanks, I think that did the trick.  I also reset the xorg using **sudo dpkg-reconfigure -phigh xserver-xorg**  

I now can access everything again but the visual effects.  I have a suspicion that if I reconfigure xorg with **nvidia-xconfig** that I'll run into the same problem again.

Could the problem be that my version of compiz fusion is installed from source or is that barking up the wrong tree?

Or should I just wait until the stable release?

---

### Post by dr_james2k on 2008-10-22
Some success finally.  I modified the xorg file manually.  Even my compiz works (almost) fully with its deformation effects, etc.

(3d windows and elements not working but I'll probs have to recompile compiz fusion from source.)

---

### Post by adder1972 on 2008-10-22
Hi,

I run Intrepid on a Thinkpad X60.  Compiz stopped working after the last update. I am not able to get it to work again.



EDIT: After running:

sudo dpkg-reconfigure -phigh xserver-xorg


and restarting X, I was able to restart Compiz.

---

