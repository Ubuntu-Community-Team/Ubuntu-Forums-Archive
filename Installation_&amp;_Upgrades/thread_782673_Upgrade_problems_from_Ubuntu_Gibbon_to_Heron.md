---
title: "Upgrade problems from Ubuntu Gibbon to Heron"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by magnusbk on 2008-05-05
:confused:

A week ago I upgraded my system to Heron, was really excited about the new release. Had some problems with the upgrade manager, but found a way to do it through the terminal...

Since I run Ubuntu on an old machine (Dell Laptop D600) and it runs a bit slow, I decided to install the Xubuntu desktop after the upgrade. 

Now the problem... Xubuntu booted fine in the beginning, with occasional freezes after the login screen. Now I am not able to login to Xfce desktop at all, it freezes on a blue screen eveytime. Have to Ctrl+Alt+backspace to login to GNOME. But even that freezes up at times. 

Any suggestions how to solve this? I would like to use Xfce since GNOME runs way too slow on this laptop.

PLEASE HELP!!!

---

### Post by shadowtroopers on 2008-05-05
Sorry, just wanted to ask whether your desktop is a pure xfce or gnome still installed. If gnome still installed (mixture of gnome and xfce), may i suggest you remove the gnome first.

---

### Post by magnusbk on 2008-05-07
Ok... 

did the following:

sudo apt-get remove ubuntu-desktop
sudo apt-get autoremove

The message stated that ubuntu-desktop does not exist, therefore cannot be removed. 
Autoremove resulted in 2 files being removed, didnt note them down (should have... sorry) 

Login to Xfce has worked twice now so maybe the problem is solved. ALthough I dont understand how I am able to login to Gnome as an option toegether with Xfce, despite it being removed. 

Is there something I am missing, would just like to understand how this works...
Also, am fearing this problem will creep up again due to Ubuntu-desktop still existing...

thanks for the help..

---

### Post by shadowtroopers on 2008-05-07
Try this, this command will select your default gdm(gnome) to xdm(xfce).

sudo dpkg-reconfigure xdm

Hope this may help.

---

