---
title: "apt-get with errors"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by whitesky on 2008-01-25
Hello.
I just installed my Ubuntu 7.10, but I disconnected my Internet so Ubuntu couldn't get the packages (the part that the installation stops for a while in 82%).

Now I can't update via apt-get nor install new programs, such as aMSN, wine and many others.
How can I solve this problem?

---

### Post by dannyboy79 on 2008-01-25
please post the apt-get errors. have you re-connected the internet yet? Also, the ubuntu installer doesn't go to the internet for anything, everything is self-contained on the cd. so the installer must be freezing for another reason. Do you have ubuntu installed now? Why did you unhook the internet?

---

### Post by oldos2er on 2008-01-25
If 7.10 doesn't find an active internet connection when it first installs, it disables all software sources. So, go to System, Administration, Software Sources, check all the boxes to enable the repositories, and you should be good to go.

---

### Post by whitesky on 2008-01-25
oldos2er, that was my problem. I've already fixed it and my system is working fine.

Thank you both for helping me! :)

---

