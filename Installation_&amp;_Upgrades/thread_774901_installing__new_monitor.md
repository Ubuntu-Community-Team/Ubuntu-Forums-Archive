---
title: "installing  new monitor"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by cybergalvez on 2008-04-29
Hi all,
I need to upgrade my monitor.  I will be upgrading my old 20in monitor for a new 24in widescreen, my question is what do I need to do to keep X happy?  I'm assuming that since all the refresh rates and resolution's will be different then my current monitor, X is going to complain and most likely won't start, so what command should I use to fix my config file

Thanks in advance for the help
Jose

---

### Post by confused57 on 2008-04-29
> **cybergalvez said:**
> Hi all,
I need to upgrade my monitor.  I will be upgrading my old 20in monitor for a new 24in widescreen, my question is what do I need to do to keep X happy?  I'm assuming that since all the refresh rates and resolution's will be different then my current monitor, X is going to complain and most likely won't start, so what command should I use to fix my config file

Thanks in advance for the help
Jose
If you're using Hardy, you may not need to do anything. I switched from a 19" CRT to a 19" LCD, Hardy automatically updated xorg with no manual configuration needed.

Any other Ubuntu versions, you'll need to:
```
sudo dpkg-reconfigure xserver-xorg
```
I had to run this command for Dapper & Gutsy when I switched monitors.  If you run this from recovery mode, you won't need to use sudo.

---

### Post by cybergalvez on 2008-04-29
Thanks, thats the command I was looking for
Joes

---

