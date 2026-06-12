---
title: "Kubuntu / nvidia: Xserver fails after installation"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by Helmi on 2007-07-20
Hi,

i already got feisty (ubuntu, gnome) running for some time on my machine. Today i changed harddisks and tried to install Kubuntu for a try on KDE. It failed 3 times:

- Gutsy Live-CD
- Feisty Live-CD
- Feisty Alt-CD

The problem is always the same. Starting the live-cd fails when i don't set the resolution manually on boot. After installation (also with the ALT-cd) X-Server again doesn' start. hmm i think it starts but it only flickers and i can't even change to the console window - i see them striped. Something with the Graphic engine!?

I already had this problem in the past but unfortunately can't find the solution again. i guess it was something with the ALT-CD starting with a parameter.

I'm using a GeForce 6200 on a ASUS Mainboard (P4C800) and a P4 2.8 GHz.

Any help would be appreciated.

---

### Post by Helmi on 2007-07-20
i found the solution myself. for future reference:

i managed to get to the console via starting in recovery mode. There i opened /etc/X11/xorg.conf

there i changed the "nv" entry down at the graphic adapter settings to "vesa" (generall driver) and startet the x-server successfully with "startx". Thereafter i installed nvidia-glx and nvidia-settings:

```

apt-get install nvidia-glx nvidia-settings

```

(sudo not needed as the machine was startet as root)

thereafter i changed "vesa" back to "nvidia" (not nv!!!) and restartet. Everything works fine.

Now i hope twin view will do the job ;)

---

