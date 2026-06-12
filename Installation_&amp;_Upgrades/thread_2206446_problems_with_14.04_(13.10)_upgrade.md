---
title: "problems with 14.04 (13.10?) upgrade"
date: 2014-02-19
forum: Installation &amp; Upgrades
---

### Post by buntuyu on 2014-02-19
I upgraded from 10.04, in two steps:  10.04 -> 12.04, then 12.04 -> 14.04 (Trusty).

I am using gnome metacity (and do NOT want to use Unity or even another variant of Gnome).  Here are my issues:

(1) My nm-applet stopped showing up in the panel.  When I run "nm-applet" from the command line, my wi-fi apparently works.  Luckily yesterday I was using a wifi connection that had been previously configured and was guessed correctly to be as the  one I wanted.  But, of course, that's just luck rather than correct functionality :-).  Any clue as to how to fix this?

(2) I suddenly lost "ctrl+space" functionality, in the terminal.  

(3) apt-get seems to be trying to compell me to use unity.  It wants to remove packages it dubs as obsolete, but they lots of them are gnome essentials!

there are other issues, but the above are the most pressing.

(BTW, I am not sure why the system is sometimes self-identifying as "13.10", at other times, as "14.04")

thanks

---

### Post by sudodus on 2014-02-19
Trusty Tahr is still under development. It will be released in April as 14.04 LTS, and while it might work well in many ways, you cannot expect that everything works, for example upgrading from older versions. You must also expect that things can break several times during daily updates/upgrades until it is released (and a few weaks after the release too).

You can help the developers make it work with your hardware, if you report your results at the testing tracker

[http://iso.qa.ubuntu.com/qatracker/m...nes/308/builds]("http://iso.qa.ubuntu.com/qatracker/milestones/308/builds")

and write a bug report at Launchpad

[https://launchpad.net/](https://launchpad.net/)

-o-

If you need a working system, I suggest that you install the current released version, Ubuntu 12.04 LTS or 13.10. It is not possible to reverse an upgrade (for example to downgrade from 14.04 to 12.04).

---

