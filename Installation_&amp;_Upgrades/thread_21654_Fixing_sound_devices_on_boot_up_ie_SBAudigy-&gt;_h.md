---
title: "Fixing sound devices on boot up? ie SBAudigy-&gt; hw:1 always"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by bosteen on 2005-03-23
I am sorry if this is common knowledge to others, but I have 3 fully working sound devices on my kubuntu machine at the moment, but I do not know how to fix them to a specific alsa sound 'slot' (ie hw:1 etc.)

I've used Mandrake and Fedora in the past, both of which I believe fixed them to a specific slot, so if I directed mplayer for example to hw:2 I knew which device it was going to use. 

Whenever I shutdown and then reboot kubuntu (purely for reasons of economy!), I have to check which devices equate to which hw:X settings as they change around randomly. This obvously has a knockon effect to /dev/dspX devices.

I am guessing that I will have to adjust the configuration in /etc/modprobe.d/alsa-base but I haven't a clue how to change this properly. I might be able to kludge it by copying the structure from my fedora /etc/modprobe, but I would like to try the 'ubuntu' way, if that exists.

Any takers?

Sound cards ->

Intel Onboard IC5
SB Audigy Z2
Logitech USB Headset

Recent Kubuntu build 20/3/05, updated recently. (686 smp)

Thanks, Ben

---

### Post by IdoMcFly on 2005-03-23
to invert my 2 sound cards, I'vetweak /etc/modules to put the module of the wanted first sound card.

---

