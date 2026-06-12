---
title: "unity panel &amp; launcher missing after update 16.04"
date: 2016-07-19
forum: Installation &amp; Upgrades
---

### Post by Nuitblanche on 2016-07-19
i agreed to the updates today. after I restarted the computer as suggested, the unity panel and launcher disappears after login.

at the login window the panel shows up ok. it's only after i login that it disappears.

when I open programs via the terminal, the menu bar also is missing

Please help

ps. I already tried the solutions posted below (they don't work):

[http://askubuntu.com/questions/475296/unity-launcher-and-top-panel-disappeared-in-14-04](http://askubuntu.com/questions/475296/unity-launcher-and-top-panel-disappeared-in-14-04)

[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

---

### Post by Nuitblanche on 2016-07-19
I have no confidence now in accepting any updates. It appears once the damage is done, there is no way to roll back/undo the updates and return to the state when it was working.

---

### Post by DragonBoy on 2016-07-19
Do the following:

System Settings > Appearance > Behavior Tab

Make sure the Auto-Hide the launcher is off. This might be set to on which is why it disappears. Good luck!

---

### Post by CantankRus on 2016-07-20
Seeing as you have access to a terminal there are a couple of things you can try.
Reset compiz/unity....
```
dconf reset -f /org/compiz/
```

Log out using
```
kill -9 -1
```
and log back in.


Still no unity, then try adding a new user...
```
sudo useradd -m [COLOR="#FF0000"]*username*[/COLOR]
sudo passwd [COLOR="#FF0000"]*username*[/COLOR]
```
where [COLOR="#FF0000"]*username*[/COLOR] is your new user name.
Log out using
```
kill -9 -1
```
and login as the newly added user.

---

### Post by fullcityblend on 2016-07-20
I have same problem here with most recent updates that came out few days ago, I'm now missing menu launcher, menubars and window borders after updates and reboot, just get desktop and my few desktop icons and right-click lets me get terminal window.

I'm running 16.04 in a vmware workstation player , I've just been restoring to the previous VMDK prior to these updates, but would eventually like to be able to run updates.

I tried the above suggestions with no joy except for creating a new username. If that would prove helpful, I can give it a shot.
I also tried booting to GRUB and choosing the previous 4.4.0.28 and also no joy, same problem.

TIA for any thoughts or suggestions

---

### Post by fullcityblend on 2016-07-21
I created a new user account as suggested above after having applied the most recent updates, and even the new user account is now not getting the unity launcher, or menu bar or window borders (if I launch a terminal window, as example.) Not sure where to proceed, but appreciate any ideas.

---

### Post by CantankRus on 2016-07-21
Ok, just trying to eliminate user config errors.
In your normal account you may want to install the flashback session for now.
```
sudo apt install gnome-session-flashback
```

Try logging in to the flasback metacity session and checking your graphics drivers with inxi. (may need to install)
```
inxi -G
```

I would also run
```
sudo apt update
``` 
again and check for errors.

---

### Post by fullcityblend on 2016-07-22
interesting, Thanks CantankRus, 
It just took me a bit to learn about Flashback and how to choose it from the login screen after getting it installed, and logging in,  Looks a bit different than before now, but was expected and I now have the menu-bar across the top with Applications - Places - and the usual settings menu with Suspend,Restart,Shutdown...
I'm good with using this instead for now, just a head-scratcher as to what happened, and this is a really plain-jane VM with a new 16.04 recently installed a couple months ago, so really no customization, mainly just used for internet-banking, so is only used less than once-a-week...thanks again for your help.

---

### Post by brennerd on 2016-07-29
Please have a look [here]("http://askubuntu.com/a/804442") to see how I solved it.

---

