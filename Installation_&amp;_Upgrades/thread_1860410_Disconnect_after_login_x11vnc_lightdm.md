---
title: "Disconnect after login x11vnc lightdm"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by vortex-5 on 2011-10-14
Hi I'm having an issue with the lightdm window manager I run x11vnc

lightdm will allow me to login but will disconnect my vnc session before it loads the desktop

I also have gdm on the same machine without an issue it will bring me to the desktop fine.

Does anyone know the work around to get lightdm to behave?




Also an unrelated problem I accidentally broke my default xubuntu themes does anyone know how to restore them?

aptitutde reinstall xubuntu-desktop xubuntu-artwork xubuntu-gdm-theme doesn't seem to work maybe I need to tweak a configuration setting somewhere.

---

### Post by vortex-5 on 2011-10-14
I realize this is very similar other GDM issues in the past that required editing the GDM.conf file to KillInitClients = false in the [daemon] section.

I don't believe this config section is available to lightdm.

---

### Post by vortex-5 on 2011-10-14
Found the problem when I purged GDM it also removed the GDM user (maybe the lightdm user)

in short the /home/myuser/.Xauthority file was assigned to root:root

deleting this file and allowing it to be recreated fixed this issue.

---

