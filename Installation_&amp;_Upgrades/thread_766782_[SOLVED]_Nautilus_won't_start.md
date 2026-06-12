---
title: "[SOLVED] Nautilus won't start"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Victormd on 2008-04-25
So yesterday I did a fresh install of Hardy and got everything working and all my progz installed, including compiz, my 8800GT graphics card, and all other hardware. I rebooted and everything worked fine.

This morning I tried to boot it and BOOMMMMM, I can't do anything!!! Nautilus didn't load and I have no icons/menus/panels... can't even open a terminal from X (can only get to a terminal by CTRL+ALT+F1). The funny thing is that Compiz is running because the cube and expo are working (????)...

Anyone have this happen to them? Any suggestions???

---

### Post by Victormd on 2008-04-25
Sorry for bumping so fast but I really don't want to rely on windows to work (nor install the progz I need), all the progz that I use are in Ubuntu...

BUMP

---

### Post by Victormd on 2008-04-25
So this was the error:
> "Nautilus can't be used now due to an unexpected error.
Nautilus can't be used now, due to an unexpected error from bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem."

---

### Post by Devi 710 on 2008-04-26
I had this same problem after I did a fresh install and a few reboots after making the changes that I wanted.

I just restarted and everything has been fine since.

I hope you find a solution. I believe the error message tells you to disable the "Bonobo ..." something to do with networking that runs at startup.

If you could install the "bootup manager" I believe it is called (I used to have it in Gutsy) you can disable it. But with no desktop or terminal, it may prove to be difficult.

I wish you luck,

Devi

---

### Post by Victormd on 2008-04-27
I tried killing bonobo-activation-server, rebooting, safe-mode, xfix, etc... and nothing worked for me. This was a very weird problem and I could not solve it so I simply reinstalled and everything is fine now... so far...

---

### Post by DenKain on 2008-04-27
I am having the same problem. I boot up, login and all I see is my background image and two files I had on the desktop. I tried using ALT+F2 to try and start Nautilus and nothing happened. I used alt+ctrl+F2 to get into the terminal. I tried a sudo startx and got nothing put X with a background picture.

HELP!!

---

### Post by Kenda on 2008-04-27
Victor, Are you still having a problem with this? Have you found a solution?

---

### Post by DenKain on 2008-04-27
Also, I guess I forgot to say that neither my top or bottom panels are showing up. I tried to run killall gnome-panel using a bashfile and nothing worked. I know I can start nautilus using a bashfile but thats about it.

I got into the configuration editor but could not find an option in there to help restore nautilus and my panels.

---

### Post by Victormd on 2008-04-27
> **Kenda said:**
> Victor, Are you still having a problem with this? Have you found a solution?

I kind'a gave up. I had just installed and got the problem, waited a day or so and couldn't solve it so I figured it was easier/faster to reinstall. Now everything is working perfectly!!

I heard that removing the mono-common package and reinstalling it would do the trick but then it was too late for me to try so if you want, you can try
CTRL+ALT+F2 to get to a terminal and type
```
sudo apt-get remove mono-common
sudo apt-get autoremove
sudo apt-get install mono-common
```

Also, read that removing and re-installing nautilus did the trick for some as well (again, saw this after I had reinstalled)
```
sudo apt-get remove nautilus
sudo apt-get autoremove
sudo apt-get install nautilus
```
Please note that I did not try this so don't know if it will work or not...

I read that some people would simply
```
sudo killall bonobo-activation-server
``` from the terminal and then CTRL+ALT+F7 to go back to X, CTRL+ALT+Backspace to restart X and everything would work again... I didn't have that luck...

---

### Post by DenKain on 2008-04-28
Yeah I just reinstalled and all seems to be good.

---

### Post by zariok on 2008-05-03
I had this problem only after installing Mono 1.9.1.

If you modify the ~/.bashrc and ~/.profile to remove all the references to the /home/YOURUSER/mono-1.9.1/* from PATH, PKG_CONFIG_PATH, MANPATH and LD_LIBRARY_PATH gnome loads just fine.  Apparently anything but mono 1.2.6 causes it to puke.

Once Gnome is loaded and you need to set your path for some development, execute ~/mono-1.9.1/bin/setup.sh

---

