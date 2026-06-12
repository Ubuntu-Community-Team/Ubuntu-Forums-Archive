---
title: "Link between Master Mono and PCM"
date: 2006-05-19
forum: Installation &amp; Upgrades
---

### Post by kwaanens on 2006-05-19
I've asked this question some time ago, but maybe things have changed or someone might know what to do now.
I have a Dell Inspiron 9300 with a built in subwoofer. My problem is that the volume applet only controls either Master Mono (the subwoofer), or PCM (speakers). Also muting, either from applet or from the physical mute button on, only affects one of the two.
I'd really, really like to link the two, so that changing one of them changes the other. 
Any advice?

- Ketil

---

### Post by blakegrover on 2006-05-30
I also have a 9300 and I have the master and master mono I would link together so when I turn up, down or off the sound it does it to both controls.

Any help would be appreciated

---

### Post by Offthedeepend on 2006-06-05
Ditto here.  Same system, same problem.  Is there some way to specify which channels the Alsa "master" switch actually controls?

---

### Post by barakaspeed on 2006-06-07
I'm in the same boat too.  I remember vaguely from 5.10 there was a workaround script.  I can't find it anymore though.  I really wish this was resolved.

EDIT:

I found the scripts that I use with xbindkeys to make this all work out.  (One caveat, you don't see the graphic volume bar when changing the volume)

Volume Mute:
> amixer sset "Headphone" toggle; amixer sset "Master" toggle; amixer sset "Master Mono" toggle 


Volume Down:
> amixer sset "Headphone",0 5%-; amixer sset "Master",0 5%-; amixer sset "Master Mono",0 5%-

Volume Up:
> amixer sset "Headphone",0 5%+ unmute; amixer sset "Master",0 5%+ unmute; amixer sset "Master Mono",0 5%+ unmute

---

