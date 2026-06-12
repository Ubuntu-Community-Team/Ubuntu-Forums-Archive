---
title: "boot resolution problem"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by gotha on 2006-08-26
When I start the live cd Ubuntu 6.06 everything goes ok but when the GNOME starts it starts on a higher resolution than my monitor can support. My montor is realy old and it`s maximum resolution is 800x600. I tried to kill the X (ctrl+alt+backspace) and edit xorg.conf but after few seconds the X starts again and again and again ...
How can I boot with a lower resolution?
Is there any way to install Ubuntu on my hard drive without starting the X?
Thanx in advance!!!
(Excuse me for my english - I`m still learning it)

---

### Post by nyinge on 2006-08-26
Press F4 on the welcome screen for LiveCD and choose 800x600x16.

To install Ubuntu w/o starting X, I believe there's an option to install in "Text mode."  If the option is not included in the "desktop" CD, it is definitely on the "alternate" CD.  There could be other options too.
Post again if things don't turn out good.

---

### Post by Tomosaur on 2006-08-26
You don't need to kill x, just press ctrl+alt+f2 to drop to a virtual terminal. You can edit xorg.conf in there. Then, you can press ctrl+alt+f7 to go back to x, then ctrl+alt+backspace to force X to restart (this will log you out too, so save your stuff first).

---

### Post by gotha on 2006-08-28
Thank you. It works (the way with virtual terminal) so now I am with fresh installed Ubuntu 6.06. But now there is another problem. 
I can`t connect to the net. I`ve never configured this because the settings was made by the operating system (Ubuntu 4.10/5.04/5.10, suse 10.0 slackware 10.2). My provider has a dhcp server so everything configures automaticly. Now - nothing. I tried to fix the problem using the GNOME network setting. I made it to use dhcp, but nothing changes. Any idea how to fix that?](*,)

edit: It is more interesting that right now I am using ubuntu 6.06 live cd and the i-net is OK.

---

