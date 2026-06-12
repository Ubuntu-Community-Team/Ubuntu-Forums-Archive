---
title: "GEtting Ubuntu on a REALLY old PC 250mhz, 128mb ram"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by derrick1985 on 2005-04-24
Hey

Ok, i have a REALLY old computer that I would like to put Linux on as well, the Ubuntu CD works fine, it's just the system (as you can imagine) is EXTREMELY SLOW (Gnome) and I would like to be able to put Ubuntu on there.

Is there anyway to have the machine run ICEwm instead, or Fluxbox, or something that if i have to i can menu edit in all the programs, or am I stuck with putting Windows 98 back on it?

---

### Post by Leif on 2005-04-24
If you have ubuntu installed, getting fluxbox is as easy as "sudo apt-get install fluxbox". logout, and choose it in the sessions list.

---

### Post by derrick1985 on 2005-04-24
[QUOTE=Leif]If you have ubuntu installed, getting fluxbox is as easy as "sudo apt-get install fluxbox". logout, and choose it in the sessions list.[/QUOTE]

Yes, i know that. But i don't have Ubuntu on the PC yet, and i dont' want to have to isntall gnome and gdm at all. Basically, i'm asking if there is a way to have a no gui install, and apt-get the rest manually.

---

### Post by derrick1985 on 2005-04-25
[QUOTE=derrick1985]Yes, i know that. But i don't have Ubuntu on the PC yet, and i dont' want to have to isntall gnome and gdm at all. Basically, i'm asking if there is a way to have a no gui install, and apt-get the rest manually.[/QUOTE]
 *bump*

Anybody?

---

### Post by Fab on 2005-04-25
try the net install howto that is somewhere on the forum here..
it will install only the basic system, and you can apt-get from command line the stuff you need

---

### Post by tread on 2005-04-25
At the start, ubuntu provides you with two options I think, workstation/server. Install the server, which comes with no X (as far as I know) and then use aptitude to install the rest.

Otherwise, do the net install suggested above.

---

### Post by az on 2005-04-25
It is very very easy.

You do need to have an internet (broadband) connection, since you do not have much on the cd that you are asking for.


Tyoe server at the install prompt as you boot the installer.  Go through the install as normal.

Once you have installed it, you should edit the sources.list file in /etc/apt and uncomment the universe repository.
sudo nano /etc/apt/sources.list
(CTRL-O to save and CTRL-X to exit)


then do
sudo apt-get update
sudo apt-get install x-window-system-core xterm wdm icewm mozilla-firefox menu

Other nice packages are abiword for word processing, fluxbox as an alternate WM, XMMS for music, .... The list is endless.

Install synaptic to have access to a graphical package tool.  Otherwise, you can use synaptic from the command line.  
If you install XFCE, you get a whole Desktop environment that has just enough stuff, but not a lot of crap that it goes pretty fast.

Lemme know what else you would want...

---

### Post by poofyhairguy on 2005-04-25
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by derrick1985 on 2005-04-28
Well, I got XFCE installed, but it's being a pain.

Right now, I have Firefox, Thunderbird, and Openoffice (I know, but i like openoffice) but they aren't in any menu's. Luckily, I can start firefox through the Mozilla Browser link in XFCE, Thunderbird through a command prompt, but I would also like to start openoffice and also have these programs (plus future ones) in a menu.

Is there a menu editor for XFCE? The one that comes with it won't let me go out of my home directory!

---

### Post by az on 2005-04-28
You should have a complete menu when you right-click on the desktop background.

---

### Post by derrick1985 on 2005-04-29
[QUOTE=azz]You should have a complete menu when you right-click on the desktop background.[/QUOTE]

I have the menu's, but nothing in them.

Should I have XFCE or XFCE4?

---

### Post by az on 2005-04-29
Xfce4

---

