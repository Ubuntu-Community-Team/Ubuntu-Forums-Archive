---
title: "Can't login to Gnome"
date: 2011-09-18
forum: Installation &amp; Upgrades
---

### Post by anieruddha on 2011-09-18
Hi,

I am not able to login to Ubuntu. I installed ubuntu lucid on my dell inspirion 1510 about 2 weeks back. And now not able to login to system. I try to login to shell by pressing Ctrl+Alt+F1 and I am able to login using same username, password.

But whenever I am trying to login in gnome, login window come again & again.

---

### Post by dniMretsaM on 2011-09-18
Are you sure your typing your password correctly? You could be fatfingering some wrong letters.

---

### Post by ajgreeny on 2011-09-18
Try to login at a command line from the Ctrl+Alt+F1 and then use command ```
startx
``` to see if that gets you into gnome.

---

### Post by anieruddha on 2011-09-18
> 
Are you sure your typing your password correctly? You could be fatfingering some wrong letters.

Yep I m typing right, thats why I can log into shell

> 
 startx

@ajgreeny I am giving that command, & after that I can see only black screen with mouse cursor enable. 
I waited for 20 min, but the same screen, no desktop loaded

---

### Post by anieruddha on 2011-09-18
Quick Update
I am not sure if I am on right path or not. But I did following steps

1. remove xserver & gdm

```

sudo apt-get remove --purge xserver-xorg
sudo apt-get remove --purge gdm

```

2. Reboot

3. Install again
> 
sudo apt-get install xserver-xorg
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install gdm


And now 
1. Login screen shows up
2. I try to log in
3. It shows blank screen with top-left corner xterm window

Any suggestion

---

### Post by anieruddha on 2011-09-18
Seems to I have no luck with gdm. But thanks to google problem solved.

I install another login manager called slim

```

sudo apt-get install slim
sudo dpkg-reconfigure gdm
-- and select slim

```

The desktop loading is bit a slow though

---

### Post by ajgreeny on 2011-09-19
You could also try using xdm or perhaps lxdm, both of which offer alternatives to gdm, and may be quicker to desktop.

---

