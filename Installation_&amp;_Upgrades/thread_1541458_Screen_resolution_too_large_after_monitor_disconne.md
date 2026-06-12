---
title: "Screen resolution too large after monitor disconnect among other things"
date: 2010-07-29
forum: Installation &amp; Upgrades
---

### Post by idontgetnopaper on 2010-07-29
I installed Ubuntu on a separate hard drive on my machine. I also upgraded it from the 9.10 that was shipped on CD to 10.4. My screen resolution is wayyy too big for my monitor and I don't know how to fix that. Also I looked to see the version I have installed in the 'Help" tab and it shows 2.04 Gnome or something.  Looking to get X Plane  9 working soon if I can get this stuff sorted. Any help is appreciated. I am really really new to this but managed to get Google earth to work so I'm headed in the right direction . <fingers crossed>

---

### Post by roger_1960 on 2010-07-29
Hi

To see what version, system>administration>system monitor

To change resolution system>preferences>monitors

---

### Post by idontgetnopaper on 2010-07-29
Thanks Roger_1960 for your reply. Unfortunately Ubuntu will not let me change the screen resolution for some reason. I had two monitors connected to my system which fixed the problem but I have to give it back to the owner. So there is something else going on that I don't know how to fix. I checked the version before I posted and it shows Gnome 2.4 even after showing the 10.4 updates were downloading. Guess I'm going back to Windows if I can't get this sorted soon.

---

### Post by P4man on 2010-07-30
What videocard do you have and what (if any) drivers did you install?
Can you get a fullscreen terminal by hitting control alt f1 (use control alt f7 or f8 to return to the gui) and if so, can you enter
```

xrandr
```

and report its output?

It sounds as if your X is configured for dual monitors and its trying to use that resolution on a single monitor. Something you could try already is getting in to a terminal and typing this

```
sudo mv /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf /etc/[COLOR="Red"]X[/COLOR]11/xorg.backup

```
please note those red X's are in uppercase and everything is case sensitive!
It will prompt for your password. just enter it (nothing is shown on screen) and hit enter.

Then restart X or reboot. Should that make things worse (which I highly doubt) you can reverse that by doing:

```
sudo mv /etc/[COLOR="Red"]X[/COLOR]11/xorg.backup /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf

```

---

