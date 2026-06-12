---
title: "Unable to login to Gnome"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by vgoel9 on 2007-08-22
Hello, I have screwed up my Ubuntu installation. 

When I log in, I get the following message:
"Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix the problem.I cannot log into my Gnome desktop and have lost my username. 

I have no name!@motx:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x “/var/lib/gdm/:0.Xservers” -h “” -l “:0&#8243; “vgoel”
/etc/gdm/Xsession: Beginning session setup…
Could not get password database information for UID of current process: User “???” unknown or no memory to allocate password entry

Failed to start message bus: Memory allocation failure in message bus
EOF in dbus-launch reading address from bus daemon
------
All services appear to be running and I can ssh into the system:
——-
Please let me know if you have a pointer for me. Thanks.

---

### Post by eggdeng on 2007-08-23
> I have no name!
If this your username, the problem is probably down to the spaces and invalid characters. 
Boot in recovery mode and you will be able to create a new administrative user. From a terminal ```
useradd -g admin your_username
``` Use only alphanumeric characters and no spaces. As this is a fresh install, probably better just to reinstall though.

---

