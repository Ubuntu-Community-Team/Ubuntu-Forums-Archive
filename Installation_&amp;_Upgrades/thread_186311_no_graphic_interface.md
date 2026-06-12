---
title: "no graphic interface"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by benner on 2006-06-01
I first installed breezy badger, then tried again with dapper drake on a dell p3 450 and in both cases, after the install there was no graphic interface, just a command prompt to login.  i did and it came up as user@ubuntu: and i didn't know what to do next.  probably something simple, i bet...

---

### Post by az on 2006-06-01
[QUOTE=benner]I first installed breezy badger, then tried again with dapper drake on a dell p3 450 and in both cases, after the install there was no graphic interface, just a command prompt to login.  i did and it came up as user@ubuntu: and i didn't know what to do next.  probably something simple, i bet...[/QUOTE]


That's not supposed to happen.

I'll bet it's a bug in the xorg packages (the graphical server - your card is probably misdetected.

Do you know what kind of video card you have?

Log in  and run

lspci 

and look for a line that says something about a VGA adapter.

Also, just for kicks, run

sudo apt-get -f install

to see if the install was not completed for some reason (maybe a faulty optical drive?  I dunno)

---

### Post by ubuntu_demon on 2006-06-01
The autodetection of your monitor and/or videocard goes wrong.

First backup the configuration file :
$sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

You can copy it back if needed by :
$sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

Now try $sudo dpkg-reconfigure xserver-xorg and choose all the default or simple options. This will alter the /etc/X11/xorg.conf file.

After that reboot and see if your problem is solved. You might try a few times.

If not please try posting your : 
/var/log/Xorg.0.log and ~/xsession-errors log files.

I'm going to sleep soon so I hope someone else can help you further. Sorry.

---

