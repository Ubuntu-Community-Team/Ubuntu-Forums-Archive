---
title: "Can't get into GUI interface"
date: 2005-03-29
forum: Installation &amp; Upgrades
---

### Post by skexsis on 2005-03-29
I just installed Ubuntu 'server' since the basic would not install properly. I could originally boot into the graphical interface but when I reinstalled it is text based and i don't know how to go get my laptop to configure the screen and use the GUI. I am using a casio - cassiopeia fiva-102. The version of Ubuntu is 5.04.  If you can help I would be very gratefull. If you couldn't tell I'm trying to make the transition from windows to Linux.

---

### Post by orion_114 on 2005-03-29
try startx
to see if you have installed an xserver

---

### Post by ola on 2005-03-29
You can install the whole ubuntu package with

```

sudo apt-get install ubuntu-desktop

```

I'm not sure if that's what you want though..

---

### Post by alastair on 2005-03-29
If the GUI (X) does not start for you (try : startx etc.), then :

a) Check the X log file for warnings/errors : /var/log/Xorg.0.log

b) Check the configuration of X : /etc/X11/xorg.conf

As previous commenters say though - make sure you have the right s/w installed (desktop, xserver etc.).

---

### Post by marvelchip on 2007-12-24
I have ubuntu server V7
After running startx, im getting: 
X: cannot stat /etc/X11/X (No such file or directory), arborting. 
xinit: Server error. 
what do i do?

---

### Post by mamlouk on 2007-12-24
Ubuntu server does not ship with any GUIs. As Ola said, you'd have to apt-get it.
```
sudo apt-get install ubuntu-desktop
```

---

### Post by cookiemonster0774 on 2007-12-24
Thanx alot folks.
 I am totally new to linux and after 3 weeks of fighting to get Ubuntu on to a laptop with no cdrom I was afraid this was going to be another major nightmare. This was relatively painless.

---

### Post by marvelchip on 2007-12-27
Inserted the ubuntu server/desktop CD in drive, coded my sudo apt-get install ubuntu-desktop, but now getting  

E: Couldn`t find package ubuntu desktop

I`m really stuck now

---

### Post by Partyboi2 on 2007-12-27
> **marvelchip said:**
> Inserted the ubuntu server/desktop CD in drive, coded my sudo apt-get install ubuntu-desktop, but now getting  

E: Couldn`t find package ubuntu desktop

I`m really stuck now
Do you have a working internet connection? If yes, then you may need to make sure that your sources.list is correct by removing the # from in front of all the lines that start with #deb
open your sources.list
sudo nano /etc/apt/sources.list
[COLOR=Red]All[/COLOR] lines that start with #deb eg.
```
#deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse
```remove the # from in front of them. so it will look something like this:
```
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse
```Once you have done that save and exit nano
```
Ctrl o
then enter
then ctrl x
```then update the list
```
sudo apt-get update
```then try installing the desktop package
```
sudo apt-get install ubuntu-desktop
```

---

### Post by jken146 on 2007-12-27
> **marvelchip said:**
> Inserted the ubuntu server/desktop CD in drive, coded my sudo apt-get install ubuntu-desktop, but now getting  

E: Couldn`t find package **ubuntu desktop**

I`m really stuck now

Is that a typo?

---

### Post by marvelchip on 2007-12-31
Well, thanks. I finaly got to the GUI. after a thirteen hrs of downloading the; i supose updates.

So does this mean when i want GUI on another server i have to go thru thus process again?

---

