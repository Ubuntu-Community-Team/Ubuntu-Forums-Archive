---
title: "installation problems 8.04 alternate on new hd"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by udippel on 2008-05-17
As a rather seasoned sysadmin I was astonished to encounter that much of troubles installing 8.04 alternate on a fresh hd:

1. It got stuck at 'Configuring apt'/'Scanning the mirror' at 28%. Found a 'solution' here: unplug and plug back the network cable. It did work, but still, that is strange. In the description of the problem it was mentioned it needs a proxy. No, here we don't need a proxy, so I don't know what made it stuck. I install OpenBSD, Solaris, etc. regularly, but never ever had to set a proxy. Whatever; solved.

2. The install hung completely at 85% 'vino installed' later. I could still open a terminal, but it would not move beyond.

3. I checked the integrity of the CDROM, from the menu, and it passed.

If I can help to debug the problems, please tell me what to do.

Uwe

---

### Post by udippel on 2008-05-17
'Solved', so to say:
Just boot the install-CDROM with purposely unconnected network(s), and it goes through without a hitch.

Thumbs up: after reboot, and plugging back the network cable, everything runs perfectly well, it finds the repositories, network settings, all on its own.
My suggestion: Change the installation instructions in a way to discourage networking during install.
:lolflag:

Uwe

---

### Post by Donny Bahama on 2010-03-19
I'm stuck at the exact same spot, but unplugging/reconnecting the ethernet cable didn't help.:confused:

---

### Post by Donny Bahama on 2010-03-19
OK. I guess what you have to do is unplug the cable, wait a few minutes for install to resume, then plug it back in. (Worked for me anyway.)

---

