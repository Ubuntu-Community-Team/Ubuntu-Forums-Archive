---
title: "can't log in into my ubuntu 12.04 after reboot"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by abdouboulegh on 2013-11-22
[COLOR=#333333][FONT=UbuntuRegular]first reboot after installing ubuntu 12.04, ( 40 hours later) actually there was an electricity shortage, now everytime i type in my credentials it goes black for a second or two then goes back to the login screen, I've already tried many of the solutions on this forum, like deleting .Xauthorization Doing a Chown on my home directory, resetting unity, ubunty-desktop, and still nothing, i think during the setup i checked that crypted home thingy, i also installed many things ... vmware, oracle 12c, eclipse ... etc[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]any help would be really welcome it's super urgent :/[/FONT][/COLOR]

---

### Post by mellocode on 2013-11-22
Ok one thing to try would be to login as a different user to see if that works. Can you do CTRL-ALT-F1 to switch to a different tty and login? Then if you add a new user (or just replace your home directory with a clean one; don't erase it just mv it to a different path so that you can attempt logging in without any of your profile settings.

---

