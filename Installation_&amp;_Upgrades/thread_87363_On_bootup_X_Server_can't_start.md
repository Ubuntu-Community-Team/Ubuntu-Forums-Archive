---
title: "On bootup X Server can't start"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by David Haas on 2005-11-07
I just changed 'Hoary" to "Breezy" in /etc/apt/sources.list and then updated the repositories in Synaptic. Then I upgraded Gnome, Open Office, and Firefox in Synaptic. All worked well, until I booted up again. Then I got a dialogue that says "I cannot start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?" In the dialogue is a highlighted "Yes" and an un-highlighted "No". When I pressed enter nothing happened. The screen is locked. Any idea how I can fix this problem, short of re-installing Ubuntu?? I'm now using the Hoary live CD. 
Thanks,
David Haas

---

### Post by GoldBuggie on 2005-11-07
try

```
sudo dpkg-reconfigure xserver-xorg
```

also make sure that you choose advanced when asked about configure your monitor.

---

### Post by David Haas on 2005-11-07
GoldBuggie--Thanks for the advice. I think I followed it in the terminal. The program recognized my video card, monitor, and mouse type. I went through the whole set of questions. But, nothing has changed when I boot up from the hard drive. Anything else to try, or should I just re-install Hoary? I wasn't aware that while on the Live CD, changes could be made to the hard drive.
Thanks,
David

---

### Post by David Haas on 2005-11-08
Well, I simply re-installed Hoary from the CD and updated packages.  It runs perfectly now, but we lost a few unsaved files. :( 
David

---

### Post by eyebrowman92 on 2005-11-08
i also had this problem when i installed hoary from the cd.  after i installed i didnt upgrade to breezy and found that the x server wasnt set up right in hoary. once i uograded to breezy the x server has worked fine.

---

