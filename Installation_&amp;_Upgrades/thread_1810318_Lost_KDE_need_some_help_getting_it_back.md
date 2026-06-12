---
title: "Lost KDE need some help getting it back"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by peejaygee on 2011-07-22
Hey Guys (&Gals)

I have a question, I've ventured back to Linux after many years and decided to mess around with Kubuntu 11.04, so anyways. I install it (I'm Dual Booting with Vista) and I have *nothing* of importance on it... but within 24 hours (after looking to see what I could do) I tried to install Gnome (latest version, which apparently isn't fully supported) and it didn't appear to work (got to 61% on the install) annnyywwaayyy... I decided to quit it and went to the, errr, session manager? no, the bit were you login and you can choose your environment, so I choose 'default' and login, only to be presented with a totally blank screen, no menus, nothing, just a mouse pointer...

I figured there would be a key combo to give me the 'log off' option, then I could re-choose another env, but nope...

Anybody help me, I know I can re-install the whole system, but I would like to learn from my mistakes and see how I can recover from my error.

if I CTRL and ALT and F6 (it appears) it drops me into a full screen terminal session (when I've logged in)..

Look forwards to any replies and/or criticism received.
Regards

---

### Post by tommcd on 2011-07-23
If you tried to install Gnome 3 from a third party unsupported repository, then that is likely what caused the problem.
In any case, try booting to recovery mode and run:
```
apt-get install --reinstall kubuntu-desktop
```
This should hopefully reinstall your kubuntu desktop to it's pristine state. Then reboot and see if you can log into Kubuntu.
You should also probably remove Gnome 3 if it is not working.

---

