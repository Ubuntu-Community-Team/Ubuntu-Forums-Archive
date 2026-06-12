---
title: "after upgrade to 12.04 no logout button !?"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by petermg on 2012-04-27
Ok so I upgraded from 11.10 to 12.04 on a netbook, and 11.10 was working great on it.  After it said to reboot I had many issues most of which I THINK were fixed by a sort of "sudo apt-get -f install", "sudo dpgk --configure -a", "sudo apt-get upgrade", etc.  In any event, I can log into lightdm via the Unity greeter, but for some reason I don't have a logout button up in the corner anymore.  I have the time, the volume, the network icon, the battery icon, the email icon, but no logout icon.  What should I do?  Should I uninstall ubuntu-desktop then reinstall it via "sudo apt-get remove --purge ubuntu-desktop", then "sudo apt-get install ubuntu-desktop"?

---

### Post by dino99 on 2012-04-27
i've reinstalled the menu icon via "add to panel" : alt+right-click to do it

---

### Post by petermg on 2012-04-27
I ran a bunch of updates/upgrades via synaptic and that seemed to solve the problem.  Weird.

---

### Post by RAD-MAN on 2012-04-28
Also had this problem, soulution is to change your theme so it reloads.

---

