---
title: "Gui install on Ubuntu server after install"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by prmmelp on 2020-05-29
I have successfully installed Ubuntu server on a new machine and it boots up fine.  Trying to install the Cinammon Gui on the machine, but I am having a hard time finding decent instructions.
Can someone help.
Basically I want the gui to boot from startup.
My next step after I get the gui up and running is to get my rocketraid 8240A card going so I can propogate the array of 4  6TB drives
Thank you.,

Mel

---

### Post by lazyteddy on 2020-05-30
```
sudo apt install cinnamon-desktop-environment
```
As this will also install lightdm, it *should* boot into the GUI afterwards where you can log in to Cinnammon. Official Ubuntu flavors can be installed with packages like (k/x/l)ubuntu-desktop.

---

### Post by prmmelp on 2020-05-30
Thank you. I'm giving it a whirl..it's installing now....
Appreciate it much...hopefully setting up the hardware raid controller card is not too difficult.
Mel

---

### Post by prmmelp on 2020-05-30
Ill post while fresh on my mind.
The install completed and I rebooted from the command line.
The machine booted to the graphical interface with my user name and request for password. I entered the password and got the message "Failed to start session" and then it goes back to the password prompt. I am sure the password is correct as if i enter an incorrect password, it tells me so.
I tried the options for rendering mode, and it appear to move forward however the screen is wigged out with lines and dots.
Ideas?
Mel

---

### Post by lazyteddy on 2020-05-30
Not sure; this might be Cinnamon related. I've had problems getting into Cinnamon from two different laptops, and HP and a Dell. I would put the password in, and it would simply go back to the login screen after a short time. You could test this with another desktop, e.g. install xubuntu-desktop or ubuntu-mate-desktop, both of which also use lightdm. If you can log into XCFE or Mate, you know the problem is with Cinnamon. Personally, I never took the time to figure this out and simply switched to another desktop. I'm not that picky about which DE I'm using, as long as it's GTK based, and I just didn't have the patience to deal with this problem when there were perfectly usable alternatives available. Iff it turns out you can log into any of the other desktops, but really want to use Cinammon, at least you'll have a starting point.

---

