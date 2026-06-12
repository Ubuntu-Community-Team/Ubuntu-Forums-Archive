---
title: "Problem installing nvidia drivers"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by hlstriker on 2008-09-03
Hi, I'm trying to install nvidia drivers from the nvidia website and I'm having a really strange problem I've never had with any other distro.

After installing the drivers, setting my xorg.conf file, and reloading x the new installed drivers will work perfect. The strange thing is when I reboot the computer it creates a xorg.conf.failsafe file and uses that while making me run in some low graphics mode. I tried to remake the xorg.conf file and yet again it will make the failsafe file and force me to use that.

Does anyone know why this would be happening? Keep in mind it works perfect until rebooting the computer.

Here is what I'm running:
-Ubuntu 8.04.1, kernel 2.6.24-19-generic
-GeForce 7600 GS

---

### Post by pytheas22 on 2008-09-03
I don't know why that's happening, but I suggest using [envy]("http://albertomilone.com/nvidia_scripts1.html") to install the nvidia drivers.  It's much easier than using the installer from the nvidia site, plus it saves you from having to reinstall the nvidia module every time you upgrade your kernel (the module would get updated automatically via Ubuntu updates if you use envy).  envy doesn't always work, but it usually does; let us know if it solves your problem.  You may want to reinstall Ubuntu first, since I'm not sure what kind of strange stuff is going on now that prevents you from getting back to your default X configuration even when you reconfigure xorg.conf.

---

### Post by hlstriker on 2008-09-03
I actually just fixed this by modifying the linux-restricted-modules-common file and setting DISABLED_MODULES="nv".

I do wish I knew about using envy before I reinstalled Ubuntu 5 times today... Thanks a million though, I'll use that for future reference :D!

---

