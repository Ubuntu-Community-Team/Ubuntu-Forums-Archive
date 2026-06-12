---
title: "Can't log in after automatic update."
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by arpikusz on 2011-04-13
Please help! 

I've been using Lubuntu for the last 4-5 months as a virtual web server, for developing Joomla sites. I have been extremely happy with it so far. (Runs with ~300MB memory just fine)

A few days ago I installed some updates and the next time I rebooted the login screen was different and I couldn't log in to the graphical environment any more.

If I hit Ctrl+Alt+F2 I can log in to the console but when I want to log in via the graphical interface it won't do anything. 

Does somebody know what's going on???

---

### Post by Kirboosy on 2011-04-13
Sounds like the virtual mouse is not communicating correctly.

Is it possible to install Virtualbox and run the VM inside Virtualbox? (I think they use the same type of virtual disk...) 

I'm not to familiar with VMware but maybe try a different mouse mode. I know Virtualbox has Seamless mouse integration...if VMware has anything like that disable it and see if that helps any.

Hope that helps...
~Caboose

---

### Post by arpikusz on 2011-04-14
Are you sure? The mouse looks like it's working fine. It is when I enter my username and password, that the screen just flashes once and asks for the username again.

---

### Post by Kirboosy on 2011-04-14
Ok you made it seem like the mouse wasn't moving or anything. Since the screen is just flashing thats totally different...

Try logging in through command line. > If I hit Ctrl+Alt+F2

Run the following command **with** root access: 
```
update-alternatives --config x-session-manager
```

Then choose startlxde. (For the option to show-up, you may have to reboot your system first.) 

Then try running ```
startx
``` LXDE should be started.


All information found from [here]("http://wiki.lxde.org/en/Debian#No_display_manager.2C_use_startx")


~Caboose

---

