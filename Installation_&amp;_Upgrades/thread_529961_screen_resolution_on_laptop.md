---
title: "screen resolution on laptop"
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by acron1 on 2007-08-19
Hi all,

I just installed ubuntu on my 2nd laptop and for some strange reason the resolution is defaulted 
to 1024x768 and can't change it in the GUI. The native resolution of the screen is 1280x800.
In xorg.conf under the section "screen" subsection "display" for all colour depths the mode is always set to 1280x800.
What gives?
Thank you all in advance.
Steve

---

### Post by acron1 on 2007-08-21
Problem solved.
Apparently there is a bug with the Intel integrated video controller that can easily be solved by doing the following from a terminal window:
$ sudo apt-get install 915resolution

---

### Post by Burwell40 on 2007-08-21
My device will only display 1024x768 which distorts everything.  I think it's supposed to be 1280xwhatever the number is that works.  Anyway, I tried your command and got the following response.

Couldn't find package 915resolution

---

