---
title: "Unable to login after failed update gUTSY gIBBON"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by plo on 2008-01-18
Been running Gutsy Gibbon/Gnome/Nvidia since release and had no major problem. Now when I installed the latest update package it did not complete the installation. It stopped at something similar to avh..- deamon.
I'm not sure of the first word but.....After waiting half an hour I turned off the power and now I can't login. I do get the regular login display but after entering user/pwd it returns to the login screen after a couple of seconds.
Tried gnome failsafe with same effect. I do get a terminal in Terminal failsafe mode.

In the terminal I have tried "sudo apt-get update" and "sudo apt-get install" but it does not help.
After that I tried failsafe Gnome again and I did get so far so I did see the desktop with the menubar at the top before it exited to the login screen.

I'm stuck

/Lars

---

### Post by PmDematagoda on 2008-01-18
See if:-
```
sudo apt-get install -f
```
and
```
sudo dpkg --configure -a

```
would fix the problem.

---

### Post by RawMustard on 2008-01-18
re-install your nvidia drivers

---

### Post by plo on 2008-01-18
Does nor help. And I cant access drivers since the network connection does not seem to work. (due to the problem other computers are fine)
I'm stuck!

---

