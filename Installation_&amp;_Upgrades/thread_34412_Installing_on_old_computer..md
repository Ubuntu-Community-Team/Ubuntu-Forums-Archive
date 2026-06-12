---
title: "Installing on old computer."
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by Wrincle on 2005-05-14
I was wondering how I could install Ubuntu Hoary Hedgehog on an older computer, and have it running well enough to access internet, download via P2P (probably Limeiwre), access email, and burn CD's with.

I know there's some sort of GUI i'll have to use that's a bit more lo-fi than KDE or Gnome, but I don't remember. This is for a friend. I think the computer's a Pentium 2 or 3 (prob. between 500-800mhz), 128mb of RAM, 10gb HDD, cable internet, with integrated video/sound.

I wonder if there's a lo-fi install option on the install disc...

Thanks!

---

### Post by arctic on 2005-05-14
actually it should install without problems on the computer. but in case you find ubuntu still too bloated, try a stripped down live-cd with hdd install option: beatrix. based on ubuntu and knoppix, boots in a hurry and supplies you with a tweaked kernel and all important every day apps for joe average. :D

---

### Post by az on 2005-05-14
There are several project for this planned for the next release. 

Right now, you can enable universe and install xfce4, or icewm (install menu too) or fluxbox.

Try each of those and see which one best suits your needs.

On a 500 MHz computer, though, Ubuntu is still faster than windows...  Perhaps a little bit more ram would help too.


To do this from the beginning, install with the server option and that will install the base system

Then login and type

sudo nano /etc/apt/sources.list
and uncomment the line which is the universe repository (read the comments)

sudo apt-get update

sudo apt-get install x-window-system-core gdm xfce4 abiword mozilla-firefox synaptic (and whatever else you want... Use synaptic,  You will need printer functionality and stuf...)  This is just a suggesting.  There are loads of packages to choe from...



Good luck!

---

### Post by RoadWarriorEWR on 2006-07-29
How do I enable and configure printing in fluxbox?

---

