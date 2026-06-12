---
title: "Nvidia 9631 &amp; 9755 no good?  Legacy 7184 ok"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by moopere on 2007-05-19
Seems like there are Nvidia troubles all over for Feisty and people with Nvidia cards.  Hit me with -all- my Nvidia based machines so something smells fishy.  Here's what I had to do to get stable working systems on feisty:

1) Don't use Restricted Manager, it plonks things in /etc/default/linux-restricted-modules-common that you really don't want and will stop the proprietry drivers from working

2) If possible, try to use the legacy drivers (nvidia-glx-legacy).  These are version 7184 and are stable.  Some very recent cards won't work with this and as a result you'll get stuck with 9631 or even worse 9755.  My own experience and a quick search on these forums will show that there are problems with both the newer drivers and the feisty kernel (or something else in feisty?  X ver 7.2 perhaps?) ranging from screen artifacts to reboots to X restarting.

3) If your card is too new to run with the legacy driver and you can't stand the screen artifacts use the nv driver and wait until these problems are fixed which surely they will be.  ATI guys must be laughing their asses off at us right now :)

4) If you do find that the legacy drivers work better for you right now, don't forget to add 

```

Option  "AllowGLXWithComposite"  "True"

```

to the devices section for your graphics card in /etc/X11/xorg.conf.  The legacy drivers were compiled assuming composite is turned off, but X now has it turned on by default.

Regards,
Craig

---

