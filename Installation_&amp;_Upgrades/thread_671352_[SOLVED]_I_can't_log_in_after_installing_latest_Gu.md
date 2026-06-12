---
title: "[SOLVED] I can't log in after installing latest Gutsy updates!"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by mahasmb on 2008-01-18
I installed Brutal Chess last night plus the SDL and Freetype packages needed from source to have Brutal Chess working. A few hours later, Gutsy notified me that I had new updates. So I installed them, and they install fine. Some hours later, I reboot, and I can't login because the login screen just keeps on flashing repeatedly in an infinite loop and doesn't even give me a chance to type in anything.

I remember rebooting after I had installed Brutal Chess and everything was fine. It was only after I installed the updates that I had any problems, but I'm mentioning Brutal Chess just to be sure and thorough.

I tried "apt-get install -f" and " dpkg --configure -a" in the recovery terminal but neither work.

---

### Post by GICodeWarrior on 2008-01-18
> **mahasmb said:**
> I tried "apt-get install -f" and " dpkg --configure -a" in the recovery terminal but neither work.

You may have the received the bad xorg update.  See my post over here for information on how to downgrade:
[http://ubuntuforums.org/showthread.php?p=4161267&posted=1#post4161267](http://ubuntuforums.org/showthread.php?p=4161267&posted=1#post4161267)

---

### Post by mahasmb on 2008-01-18
Even after following your instruction and rebooting (it said the downgrade was indeed successful) it doesn't fix my problem.

---

### Post by mahasmb on 2008-01-19
I even tried

```
 dpkg-reconfigure xserver-xorg

```

but it still isn't working.

Edit:

It's fixed. The problem was my Brutal Chess installation, specifically either the Freetype-2.1.9 and/or SDL-1.2.7. I luckily still had those folders in my trash, so I copied them back to the Desktop (which is where I initially ran the installation), ran a "sudo make uninstall" for both, and when I restarted GDM, everything was fine again.

Any ideas as to why this happened?

---

### Post by Huss on 2008-01-20
I'm finding the same problem with Feisty. I reboot, login and then watch it loop back to the login screen. 

The last update I installed was a free type update (and two others). 

Can anyone help with a simple step by step solution?

I can login to the terminal but don't know where to go from there.

---

### Post by PARTyZAN on 2008-01-20
> **Huss said:**
> I'm finding the same problem with Feisty. I reboot, login and then watch it loop back to the login screen. 

The last update I installed was a free type update (and two others). 

Can anyone help with a simple step by step solution?

I can login to the terminal but don't know where to go from there.

I'm having the same problem. If I log in using "failsafe" option it works normally. But if I try to run anything that uses hardware acceleration or even try to do "glxinfo" x server restarts and I'm back at login screen.

---

### Post by mahasmb on 2008-01-21
> **Huss said:**
> I'm finding the same problem with Feisty. I reboot, login and then watch it loop back to the login screen. 

The last update I installed was a free type update (and two others). 

Can anyone help with a simple step by step solution?

I can login to the terminal but don't know where to go from there.

Well, like I said, I uninstalled freetype and SDL which solved the problem. How did you install freetype?

There are 3 ways to uninstall it. 
- Either through the terminal with "sudo apt-get remove freetype"
- or through Synaptic,
- or if you compiled it from source, you'd have to move back to the folder (by using the terminal) you made the installation in and run "sudo make uninstall".

---

### Post by Huss on 2008-02-01
> **mahasmb said:**
> Well, like I said, I uninstalled freetype and SDL which solved the problem. How did you install freetype?

There are 3 ways to uninstall it. 
- Either through the terminal with "sudo apt-get remove freetype"
- or through Synaptic,
- or if you compiled it from source, you'd have to move back to the folder (by using the terminal) you made the installation in and run "sudo make uninstall".

Ah. I ended up reinstalling. I'll remember the 'apt-get remove' command if it happens with another update though.

Thanks!

---

