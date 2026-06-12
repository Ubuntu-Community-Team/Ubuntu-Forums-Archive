---
title: "Window Managers/Desktop Environments"
date: 2005-11-28
forum: Installation &amp; Upgrades
---

### Post by TheAnonymousx on 2005-11-28
So i've had people suggest that I use blackbox, and fluxbox as well as open box and xfce as my desktop environment/window manager. I'm wondering how to get GDM to allow me to chose which environment/manager to load upon start up so that I can try out a few before making a decision (or just have a bunch resident).
Thankx guys.
-X

---

### Post by Leif on 2005-11-28
click on "session" at the login

---

### Post by TheAnonymousx on 2005-11-28
stupid I am yes?
Thankx, trying on next boot.

---

### Post by Leif on 2005-11-28
just to be clear, you have to install the things you want to try first. just look for them in synaptic. have fun !

---

### Post by ranf on 2005-11-28
[QUOTE=Leif]click on "session" at the login[/QUOTE]
Not all window managers are setup to work this way (what a pity).
I've tried a dozen or more. Some you need to put in `.xinitrc' in your home.

Ah, I took notes:
```

$ less windowman.txt
fluxbox         # fast, mouse menu
matchbox        # fast, minimalistic, xinitrc
blackbox        # fast, mouse menu
afterstep       # ugly fonts, bloated
ctwm            # fast, mouse menu, xinitrc
evilwm          # über minimalistic, xinitrc
aewm            # very minimalistic, xinitrc
aewm++          # very minimalistic, xinitrc

enlightenment   # nice, mouse menu, xinitrc with installer
flwm            # nice, mouse menu, xinitrc
golem           # wooden look, mouse menu, xinitrc with installer
ion3            # very minimalistic, gdm
pwm3            # ~,                    ~

wmaker          # nice, mouse menu (not taken from debian), gdm
ratpoison       # über minim

```
(the comments are just _my_ opinion)

---

### Post by TheAnonymousx on 2005-11-28
[QUOTE=Leif]just to be clear, you have to install the things you want to try first. just look for them in synaptic. have fun ![/QUOTE]

Yes, I did go and grab the package for one of them (openbox) and install it. I haven't rebooted yet to see if it's there waiting to be configured though. I'm also gonna go with xfce I do believe and see how it plays out.
Someone else got a suggestion for a good window manager/Desktop environ?

---

### Post by Kyral on 2005-11-28
XFCE is NICE (I run it on my desktop system) It has its own Compositing (which means if you have the power you can have things like drop shadows and true transparancy)

Flux is awesome for low power systems. My laptop uses it

---

### Post by TheAnonymousx on 2005-11-28
[QUOTE=Kyral]XFCE is NICE (I run it on my desktop system) It has its own Compositing (which means if you have the power you can have things like drop shadows and true transparancy)

Flux is awesome for low power systems. My laptop uses it[/QUOTE]

Awesome. I just installed xfce (via package) is there anything else I need to grab from the packages to utilize it on my next boot?

I'm thinking of moving to blackbox (or flux) for my home system. It's a 500mhz duron with 128MB of RAM.

---

### Post by Leif on 2005-11-28
you don't need to reboot, you can just logout and login again

---

