---
title: "[SOLVED] mouse artifacting"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by seventstrat on 2008-10-09
Hey guy,
I have the same problem with the mouse artifact under the mouse as a few other people in this forum:

[http://ubuntuforums.org/showthread.php?t=285144&highlight=mouse+artifact](http://ubuntuforums.org/showthread.php?t=285144&highlight=mouse+artifact)

and I've tried adding:
Section "Extensions"
Option "Composite" "0"
EndSection 

to the xorg.conf through the console.... However, I cannot seem to make this work. If I set Composite to 0...I loose the artifacts which is good, but I also loose the ability to use CompizFusion....which is definitely worth the artifact.

Is there anyway to use CompizFusion and not have artifacting?

I'm running a Lenovo T60P with an ATI FireGL v5250.... I assume it has something to do with the ATI drivers.....

On a side note....I'm a ubuntu n00b.... so... help me out! =)


Thanks
seventstrat

---

### Post by seventstrat on 2008-10-12
hey guys i know im new to the forums and all.... and general forum ethics is not to double post....but i figured something out

maybe it can help out the 27 other people that looked at my forum

follow this guide (applies to ati and nvidia)

[http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/](http://vasir.net/blog/ubuntu/set-up-dual-monitors-with-ubuntu-804/)

(also gets your dual monitor output working....but it removed the mouse artifacts as well)

oh and i can use compfusion too!

peace
seventstrat

---

