---
title: "How to start Gui from recovery mode? Video driver revert?"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by midnight27 on 2006-10-03
I have reinstalled 3 times so far after I get everything to the way I like it including all my 25+ firefox extensions, and evo mail, dual gnome/KDE install dual booted with windows.  My Amd64 settup(first install) worked perfect!!! But needed certian apps.  Being doing 386 to k7 installs everything fine.  I keep messing up with installing the nvidia driver for 3d accl.  I couldn't get into  gui last night, but fixed it with sudo apt-get install nvida-glx (temp fix as this is not the newest driver!) But it got me in. I installed some opengl dev libs, wine and a few other things, now today It is doing the same thing, but when I try my fix from last night, in the recovery console. "Can't install nvida-glx dependency problem with openglu1-mesa"  What!  I try "apt-get install openglu1 and openglu1-mesa" more errors. 

Is there a way I can uninstall and reinstall the video drivers, or at least the generic ones that you start with so I can at least boot normally? Also what are some console commands for starting the gui from the the console without typing "reboot"  Sorta like "STart" or "win" from dos prompt in windows.  Any other useful tips advice, links, suggestions, consloe commands anything to get me going?

I posted something 2 days ago when I was having truouble the first time and got no respose, quite discouraging for a user community! :(

---

### Post by tuxcantfly on 2006-10-03
sudo gdm
for ubuntu
sudo kdm
for kubuntu

---

### Post by az on 2006-10-03
> **midnight27 said:**
> 
Is there a way I can uninstall and reinstall the video drivers, or at least the generic ones that you start with so I can at least boot normally? 

Try reinstalling the linux-restricted-modules-xxxx package.

sudo apt-get install --reinstall (package).....

> **midnight27 said:**
> 
Also what are some console commands for starting the gui from the the console without typing "reboot"  

From recovery mode, you need to run:
init 2

---

### Post by tuxcantfly on 2006-10-05
> From recovery mode, you need to run:
 init 2

you don't use ubuntu, do you? that's for redhat. ubuntu defaults to runlevel 2, with an xserver.

---

### Post by tuxcantfly on 2006-10-05
anyhow, use sudo /etc/init.d/gdm start

as for the fallback drivers, do this:

sudo gedit /etc/X11/xorg.conf

find the line that says "nvidia" under the section "device"

change it to "nv"

then do sudo /etc/init.d/gdm start

---

