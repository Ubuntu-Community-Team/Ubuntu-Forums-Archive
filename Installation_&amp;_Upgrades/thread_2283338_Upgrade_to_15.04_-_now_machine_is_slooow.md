---
title: "Upgrade to 15.04 - now machine is slooow"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by acebone on 2015-06-21
Hi

Just did the distroupgrade from 14.0x to 15.04

Now my Dell XPS 13 is unbearably slow.

Browsers are using between 100-200% CPU just loading a page
XMind causes java-cpu-usage to rocket
Pulse-audio often uses 50-100% CPU, even though no sound is played.

It seems to come in waves, right after upstart the machine is quick and responsive, but very soon it will become very sluggish with moments of "almost as responsive as it should be"

I haven't got a clue what to do in terms of diagnostics I'm afraid ... but I'm ok with using bash and editing conf. files.

---

### Post by dino99 on 2015-06-21
As usual use htop to identify which process(es) are concerned; and glance at logs (dmesg, xorg.0.log mainly)
XMind can be dropped and replaced by freeplane

---

### Post by acebone on 2015-06-21
All processes seems concerned. Right now I'm copying my home-dir to an external disc - I'm giving up, nuking my machine back to 14.x - too bad :/

---

