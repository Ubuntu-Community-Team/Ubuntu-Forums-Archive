---
title: "Installation failure (blank screen)"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by kipperkidd on 2005-09-10
I am trying to install 5.04 on a Dell Inspiron  2500. All seems to proceed OK (apart from a  failure with name resolution The last ok message  I receive is 'checking battery power' [ok] Infact the  battery is crap (but I am connected to the mains). Then  the screen goes black (no cursor).  Just before this, two drumbeats sound

 How do I diagnose or fix the installation problem? I am a beginner

---

### Post by amohanty on 2005-09-10
I would suggest that you use a Live Cd and make sure that everything works first. If not use the forums to resolve any issues. Then go ahead with the install.

HTH
AM

---

### Post by kipperkidd on 2005-09-10
Thanx, I failed to mention I had used the live CD with no success. I will try again and record what responses I get

---

### Post by joshuapurcell on 2005-09-10
The two drumbeats that you hear are most likely the sound that comes on by default at the graphical login screen. You can press ctrl-alt-F1, then login to that terminal. Once you are logged in you can check the X logs in /var/logs. If you don't find anything, then bring down gdm (**sudo /etc/init.d/gdm stop**), then start it back up from the command line by issuing **startx**. This will automatically send you back to the graphical login (on the terminal at F7), so if you are still having problems you can view what errors come up by switching back to the terminal you issued **startx** from and reading the messages that come up. You could also change the settings in /etc/X11/xorg.conf related to your monitor configuration and see what happens.

---

