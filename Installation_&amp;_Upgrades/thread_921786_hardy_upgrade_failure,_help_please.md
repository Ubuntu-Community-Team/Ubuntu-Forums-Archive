---
title: "hardy upgrade failure, help please :/"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by saoró on 2008-09-16
I was trying to upgrade from 7.10 gutsy to 8.04 hardy with the update manager, I installed all the latest updates, rebooted, and then hit the upgrade button. Installation went fine, but now when I start it up there is simply a blank screen after the loading bar. No login, no mouse, just what looks like crosshatches on beige, sometimes with a thick black column down the middle.
Any ideas what I can do here? Grub says its 8.04, I can get the terminal with ctrl-alt-f1. Will I have to do a clean install? will that work?

Dell vostro 1500, 2GBram, 2.2core 2 duo, nvidia geforce 8600m gt, sigmatel audio... dual boot with xp pro sp2

Any help would be great as its totally fckd:confused: gAH, please
Noob btw

/edit... I searched and couldnt find similar problem

---

### Post by forger on 2008-09-16
Did you have any non-Ubuntu packages installed? Packages from other repositories?

Try this:
- ctrl+alt+F1
- login
- type: ```

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

```

Does it show the gdm (gnome login screen) now? Can you login from gnome?

---

### Post by saoró on 2008-09-16
I dont seem to have an internet connection at the terminal, I cant sudo apt-get, fails to "fetch" packages. I did have both repositories enabled multi/uni, had proprietry driver for nvidia card, then just stuff like mplayer, deluge, filezilla, etc...

What can I do to connect, or without a connection?

sorry about the post lag, have to reboot to try stuff...

---

### Post by Pumalite on 2008-09-16
Boot into Recovery Mode and try 'xfix'

---

### Post by forger on 2008-09-16
If the nvidia was from downloaded from nvidia.com you might have problems or using envy for ubuntu 7.10, you might see some problems..

ok, now just do:
```

sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart

```

can you login from the login screen of gnome now?

---

### Post by saoró on 2008-09-16
ÍONTACH :D  Excellent, thanks to both of you, all is like before now... sudo dpkg... etc did the job. Only the usual probs like webcam now, question for another thread I guess.

Can I ask what went wrong exactly? and why the above commands fixed it if its not too much trouble.

Thanks again

---

### Post by Pumalite on 2008-09-16
You had to fix xserver

---

### Post by saoró on 2008-09-16
umm, xserver? whats dpkg? :D

---

### Post by Pumalite on 2008-09-16
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

---

