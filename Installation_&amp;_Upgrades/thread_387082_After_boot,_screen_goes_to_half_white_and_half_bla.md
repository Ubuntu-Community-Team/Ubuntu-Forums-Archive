---
title: "After boot, screen goes to half white and half black after upgrade"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by sirgallihad on 2007-03-17
I just upgraded to 6.06 from dapper drake, and while I was installing all the new applications through synaptic, the computer locked up (a problem with my sound card, don't ask) I turned it off and on again, and now once the initial bootup screen is done loading, the computer oges straight to a screen of half black and half white. any help would be greatly appreciated!

---

### Post by nyinge on 2007-03-17
Have you tried using "Recovery Mode" at GRUB menu?  Then,
```
 aptitude update 
``````
 aptitude upgrade 
```Then, reboot.  See if that fixes.

---

### Post by sirgallihad on 2007-03-17
thanks! I ran those two commands in safe mode, and before that I ran dpkg --configure -a
there were a lot of errors, including ones having to do with the gui. I restarted, and it went straight to terminal, so is there any way to fix all these errors?

---

### Post by nyinge on 2007-03-18
How about running ```
 aptitude -f install 
```
That should try to fix the packages and their dependencies.  That doesn't work always though, if packages are really broken.  If not too much trouble, I'd just recommend doing a fresh install of Edgy.

Btw, what did you do to upgrade from Dapper to Edgy?  Was it by replacing "dapper" with "edgy" in /etc/apt/sources.list?

---

### Post by sirgallihad on 2007-03-18
I did that, and now all seems installed, but the gnome desktop still manages to be broken. it says something about it not being the default environment, so it goes to terminal. I've logged in on terminal and tried startx, and it says that there's a problem with the nvidia drivers, what should I do?

---

### Post by nyinge on 2007-03-19
> **sirgallihad said:**
> I did that, and now all seems installed, but the gnome desktop still manages to be broken. it says something about it not being the default environment, so it goes to terminal. I've logged in on terminal and tried startx, and it says that there's a problem with the nvidia drivers, what should I do?

Oh, you had Nvidia driver installed before you upgraded?  If so, you'll have to reinstall it.  I think we're getting close.  :)

---

