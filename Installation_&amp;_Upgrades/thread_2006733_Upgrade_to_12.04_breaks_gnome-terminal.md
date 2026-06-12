---
title: "Upgrade to 12.04 breaks gnome-terminal"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by jwbodnar on 2012-06-19
I upgraded my 10.10 system to 12.04, and I've got one nagging problem that I cannot solve.

gnome-terminal does not appear to be running a login shell.  I have "Run command as a login shell" checked in the Profile Preferences, but I'm not sure that's what I'm getting.

My symptom is that my system-wide PATH is not retained from /etc/environment.

Two other variables from /etc/environment are retained (ARCH and CROSS_COMPILE so that I can build the Linux kernel for my embedded work) but PATH is discarded altogether and replaced with:

/usr/local/bin:/usr/bin:/bin:/usr/games

I can't figure out from where this is coming.  No lines in my ~/.bashrc or ~/.profile set PATH this way.  Neither does anything in /etc/bash.bashrc.

My proper PATH is retained when I ssh into the machine, if I login from a console, or if I use su to change to my regular user account.

It's only in a terminal, and I tried Byobu Terminal in additional to gnome-terminal, where my PATH gets cast aside for the strange default is being used.

Where do I fix this?

---

