---
title: "Install failed to incorporate graphical interface - help!"
date: 2005-06-19
forum: Installation &amp; Upgrades
---

### Post by edisav on 2005-06-19
](*,) I tried both live-CDs, ubuntu and kubuntu, but in both cases the resolution of my monitor was at the lowest (640x480 or less). I didn't find any setting where to change that, but liked kubuntu enough to try the install.

The install seemed to go well and no error messages appeared. Upon reboot, my PC didn't boot to a graphical interface but to a terminal and a prompt. I couldn't logon to root to troubleshoot it because I didn't know the passwd, so I cold booted it and reinstalled kubuntu. Same thing, no error messages, terminal, and inability to logon as root to troubleshoot. I tried "kde" and "startx" commands to get graphical interface with no luck.

FYI, my card is an Nvidia Vanta Riva TNT2 and this may be the problem. I want to try the install again, but before I do it, I want to know:

1. What's the root pwd?
2. Where can I get a full guide of install and troubleshoot instructions?
3. What do you think the problem is and how can I fix it?

Thanks

---

### Post by huh? on 2005-06-19
from the cli prompt, type "startx"...root is "sudo" and the user name you selected..hope that gives you a place to start

---

### Post by edisav on 2005-06-19
I already said that I tried "startx" and "kde" commands and both failed as well.

---

### Post by Worzel on 2005-06-19
Had the same problem - what you need to do is edit xorg.conf with settings specific to your monitor ie adding a Modeline. Have a look at this site to get an idea of what you're after - [http://linuxreviews.org/howtos/xfree/monitor](http://linuxreviews.org/howtos/xfree/monitor). I've got a Hansol monitor which is why I came here, you'll have to google for yours.

Root password - is the same as yours, if you were the one who installed everything so when (if?) you get to editing xorg do Alt+F2, enter kdesu kate to run it as root and enter your own password when asked.

Xorg is in /etc/x11 in kubuntu.
HTH
Jim

---

