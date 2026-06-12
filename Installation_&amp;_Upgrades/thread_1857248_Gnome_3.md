---
title: "Gnome 3"
date: 2011-10-10
forum: Installation &amp; Upgrades
---

### Post by P0gman on 2011-10-10
Hello,
After I installed Gnome 3 and when I reboot my computer and I'm gonna log in to Gnome I type in my password and then I get a message saying Failed to load session Gnome/Ubuntu.

If anyone know how to fix this please post below :KS

Thanks

-P0gman

---

### Post by garvinrick4 on 2011-10-10
What version are you using" Open a terminal and:
```
lsb_release -a
```You say you installed Gnome3? What was the package you installed?

---

### Post by P0gman on 2011-10-10
I cannot login and open Terminal which is the problem I installed gnome3 by typing this in Terminal.
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install gnome-shell
sudo apt-get install gnome-session

---

### Post by garvinrick4 on 2011-10-10
What version are you using. 11.04 or 11.10.

---

### Post by P0gman on 2011-10-10
11.04

---

### Post by garvinrick4 on 2011-10-10
choose Ubuntu at login screen instead of gnome. Is on lower panel after clicking on name in login screen. Button next to choices to login to.

Now if you booted open a terminal and copy and paste one at a time.
```
sudo dpkg --configure -a
sudo apt-get update; sudo apt-get upgrade
sudo dpkg --configure -a
```
log out
see if you can boot gnome

---

### Post by P0gman on 2011-10-10
> **garvinrick4 said:**
> choose Ubuntu at login screen instead of gnome. Is on lower panel after clicking on name in login screen. Button next to choices to login to.

Now if you booted open a terminal and copy and paste one at a time.
```
sudo dpkg --configure -a
sudo apt-get update; sudo apt-get upgrade
sudo dpkg --configure -a
```
log out
see if you can boot gnome
It doesn't work dude, I've tried that :/

---

### Post by P0gman on 2011-10-10
> **P0gman said:**
> 11.04
Someone said I should do this sudo apt-get update
sudo apt-get upgrade
sudo apt-get purge gnome-session
sudo apt-get install gnome-session
startx


But after that I get this message  Could not update ICEauthority file/homeChristopher/.ICEauthority

and it didn't work and he said try this. sudo chown yourusername:users .ICEauthority
It didn't work either.

---

