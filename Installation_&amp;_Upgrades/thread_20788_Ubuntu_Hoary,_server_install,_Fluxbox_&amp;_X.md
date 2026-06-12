---
title: "Ubuntu Hoary, server install, Fluxbox &amp; X"
date: 2005-03-18
forum: Installation &amp; Upgrades
---

### Post by Yoan on 2005-03-18
I am using Unbuntu Hoary on a P4 (2.4Ghz) with 256MB of PC133 & a Geforce 440 video card. Dual booted alongside W2K; I am experienced with Slack, but this is my first adventure with a Debian-based system...


I did a server (minimal) install in under 20 minutes. Great, no bloat. Then I did:

apt-get install xorg-server

(It might not be the exact package name, but you know what I did...)

No problem. I try to do:

apt-get install fluxbox

Did not work-- had to edit the Ubuntu apt-get source files. No problem. Did it again-- it worked. Kind of. Whined about a lot of dependences. I knew it would happen, but was not too sure on how to fix it.

So I did:

apt-get update

& something along the lines of

apt-get -f install

Then installed something like xfont-base... 

or something ;) I have a poor memory for exact names, please stay with me.

Now, X & Fluxbox are both installed. There lies a cute Fluxbox folder under /etc/X11 and all. I can start X now without a problem, except it is just a grey background and a lil cursor. Not the Fluxbox I know and love. How do I tell it to run it, and not whatever it is it is doing now?

Also: what would the package be called, for Nvidia drivers?

---

### Post by bodhi.zazen on 2006-08-17
to run Fluxbox type:

startx /usr/bin/fluxbox

All one line, watch the space.

---

### Post by kerry_s on 2006-08-17
For nvidia-> sudo apt-get install nvidia-glx < then change your /etc/X11/xorg.conf to use nvidia under drivers.

---

