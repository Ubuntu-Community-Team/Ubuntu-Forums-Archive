---
title: "X doesn't start after upgrade"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by rbultje on 2007-05-05
Hi,

I dist-upgraded my Macbook Pro from Dapper to Feisty (which really wasn't all that big a deal). Now, when trying to boot my flashy new Feisty, all booting completes, up to the point where (presumably) X should start. However, it doesn't, I'm stuck at a console with a black blinking cursor. The last message says that it runs /etc/rc.local, and it appears that that should work. At this moment, I don't get a log-in prompt, I don't get an X session, I basically don't get anything. I can press the power-button to reboot, and that's about all. I'm able to gain access to the partition using Dapper live CD which I still have lying around somewhere.

How do I get my console or X back working? Once one works, the other shouldn't be too big a deal, but with neither working, I'm kinda in trouble.

---

### Post by zvacet on 2007-05-06
Boot in recovery mode and type

```
dpkg-reconfigure xserver-xorg
```

Select vesa and you will have graphic working.After that go and find proper divers for your card.when you install them go to the terminal 

```
sudo dpkg-reconfigure xserver-xorg
```

and now select your graphic card

---

### Post by rbultje on 2007-05-08
For the logs: the virtual consoles weren't there because of a (known) bug when upgrading in /etc/event.d/tty[1-6] scripts which repeat the last line twice. Once that was done, it was easy to figure out why X wasn't starting: gdm was removed. Once that was installed, I indeed ran into the often-enchanted ATI driver problem in Feisty, which I solved by various methods described elsewhere on this forum (basically install the fglrx driver + re-do some config in xorg.conf), although using vesa would've worked here also.

Thanks for the reply, and happy to say that it works and it rocks. Now if only suspend worked. :-).

---

