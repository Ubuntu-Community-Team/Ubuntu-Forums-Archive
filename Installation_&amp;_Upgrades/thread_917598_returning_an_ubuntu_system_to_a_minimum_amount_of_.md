---
title: "returning an ubuntu system to a minimum amount of packages?"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by dodonpalex on 2008-09-12
After playing around with kde4, xfce and various apps it feels like I have a system with a lot of packages that I don't really have a need for anymore. The system really feels like an ubuntu flavours mess with a kubuntu branded boot screen, xfce login manager and a gnome desktop.

Is there anyway that I could get an ubuntu system to remove everything and only keep a minimal amount of packages? It's perfectly fine if the gnome desktop and my installed apps are removed as well and I have to start reinstalling packages.

Of course I could do a re-install but it seems kinda overkill since the system if working fine.

---

### Post by Nitrolinken on 2008-09-12
You could remove the xfce4-destop and kde4-desktop packages, then use apt-get autoremove to remove any other packages that came with the ride.

You can also use dpkg-reconfigure to set back some settings if you want to jump back to scratch.
I'm not sure if $ dpkg-reconfigure ubuntu-desktop will do the trick, but it might.

---

