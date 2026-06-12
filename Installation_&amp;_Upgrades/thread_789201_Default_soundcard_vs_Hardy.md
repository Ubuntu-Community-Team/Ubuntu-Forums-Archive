---
title: "Default soundcard vs Hardy"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by blacha on 2008-05-10
Hey,
I've just installed Hardy and have a problem with sound.

I have two sound cards in my PC :

blazej@blacha:~$ lspci | grep audio
00:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)

and my while youtube video sounds play on Live other software including rhythmbox vlc etc. use V8235

I had the same problem after installing Drapper and Gutsy, but it was solved by asoundconf set-default-card option.

In Hardy though it doesn't seem to work.


Here is asoundconf output:

blazej@blacha:~$ asoundconf list
Names of available sound cards:
V8235
Live

and after running 'asoundconf set-default-card Live' and rebooting the problem remains.

Any hints on how to overcome this and set SB for the default card ?

Thanks in advance.

---

### Post by blacha on 2008-05-11
bump, anyone ?

---

