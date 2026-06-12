---
title: "Boot into command prompt not gnome"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by CMIVXX on 2005-09-12
Ok, I have screwed up my installation and can't get gnome to work properly.  How can I bring ubuntu into the command prompt at boot time rather than directly into gnome?  Also, once I get it into the CP, how do I envoke gnome again to test my fix?

Thanks.

--Chris

---

### Post by joshuapurcell on 2005-09-12
[QUOTE=CMIVXX]Ok, I have screwed up my installation and can't get gnome to work properly.  How can I bring ubuntu into the command prompt at boot time rather than directly into gnome?  Also, once I get it into the CP, how do I envoke gnome again to test my fix?

Thanks.

--Chris[/QUOTE]
When you bring up the system, have you tried pressing CTRL-ALT-F1 to get to the first terminal? Once you are there you can login, then type:

sudo /etc/init.d/gdm stop #to stop the gui
sudo /etc/init.d/gdm start #to start it back up

I'm not sure what the easiest way is to make the system not turn on gdm at startup, but you can temporarily remove the gdm file in /etc/rc2.d/gdm file.

On a side note, I'm a little fuzzy on how runlevels are used in Debian-based systems... it seems like they only go up to init 2 (versus init 6 in Red Hat, which I'm still more familiar). I would say to just switch the runlevel (using the command init) to whatever runlevel doesn't have gdm turned on by default, but that seems to not apply here.

---

### Post by az on 2005-09-12
You can reveal the grub menu at boot by pressing escape and then boot into recovery mode.

init 1 
will also do that if you are already booted.

init 2 
will bring you back to multi-user mode.


dpkg-reconfigure xserver-xorg 
will reconfigure x for you.  Run it from single user mode, or kill gdm first.

---

