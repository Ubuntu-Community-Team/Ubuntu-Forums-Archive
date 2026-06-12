---
title: "User set to system account after partial upgrade"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by thomas-cm on 2021-06-10
After partial upgrade, the user the upgrade was done on, became a system account in ```
/var/lib/AccountsService/users
```. Which means there was no user that I could log into after reboot, this prompted gnome initial set up and ask me to create a new user. When I set my old user back to ```
SystemAccount=false
``` and restart my PC, the user is once again set to ```
SystemAccount=true
```.

Ubuntu 20.04.2

Thanks for any help.

---

### Post by TheFu on 2021-06-10
/var/lib/AccountsService/users/{username} is for Gnome only.  If we don't use Gnome, then it doesn't matter. I've never heard of this directory before.

*SystemAccount=false* is the setting in mine. There's only 1 account listed on this machine. I don't use gnome sessions, but the installation was a Gnome2-based Mate DE. It uses lightdm.

Since this is extremely tied to the DE and Session involved, please provide which you are using for both.

---

### Post by thomas-cm on 2021-06-10
Yes, sorry I didn't know this.

I am on Gnome 3.36.8 and gdm3 on X11

---

