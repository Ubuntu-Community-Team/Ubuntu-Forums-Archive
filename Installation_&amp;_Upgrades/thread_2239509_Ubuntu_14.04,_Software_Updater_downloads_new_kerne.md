---
title: "Ubuntu 14.04, Software Updater downloads new kernels but they are not auto installed."
date: 2014-08-14
forum: Installation &amp; Upgrades
---

### Post by tegelstom on 2014-08-14
Hello Everyone,
(I'm new in  the forums so excuse my possible wrong posts)
I was running nice and cool on my Toshiba laptop dual booting Windows7 and Ubuntu 12.04 64bit, couple weeks ago I did a clean installation of Ubuntu 14.04, replacing the 12.04 version.
I use Bleachbit, Janitor, Remove orphaned packages, Synaptics and the command line "sudo apt-get install -f" and "sudo update-apt-xapian-index" for regular maintenance.
My problem is that Software Updater downloads new kernels(from Main Server) but it does not install them! I can see them in Synaptics as not installed. Is this a bug on ubuntu 14.04 software updater? Also what should I check at Synaptics list to install these new kernels? Here is a screenshot of my situation via synaptics:
[https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6047381789743961602?pid=6047381789743961602&oid=112478144887851328209](https://plus.google.com/u/0/photos/112478144887851328209/albums/5736976833890696177/6047381789743961602?pid=6047381789743961602&oid=112478144887851328209)
Thanks in Advance!
thomas

---

### Post by ibjsb4 on 2014-08-14
> My problem is that Software Updater downloads new kernels(from Main  Server) but it does not install them! I can see them in Synaptics as not  installed.

Remove software updater and update with synaptic, at least thats what I do :) In synaptic Edit>Mark all upgrades

Or to upgrade kernel in terminal:
```
sudo apt-get dist-upgrade
```

Edit:

You have linux-generic-lts-trusty installed?

---

### Post by tegelstom on 2014-08-16
Thanks [COLOR=#DD4814][COLOR=#000000][ibjsb4]("http://ubuntuforums.org/member.php?u=1729120") :)[/COLOR][/COLOR]

---

### Post by tegelstom on 2014-08-28
Hoorayyyy! The new kernel 3.13.0-35 installed via software updater nice and cool, everything works fine, even the iscan started to work with my wireless scanner!!!
Btw, I removed the [COLOR=#000000]linux-generic-lts-trusty!!!
[/COLOR]Which is [COLOR=#111111][FONT=Verdana]Transitional package for upgrades from 12.04 to 14.04 (Precise to Trusty), since I did a clean installation of 14.04, plus that package created a bunch of orphaned packages!!![/FONT]
[/COLOR]Well done Ubuntu, that's the spirit!!!

ps: The only minus is that with the new kernel I noticed more delay than the previous kernel during Ubuntu startup, looking forward for a speedy startup kernel ;)

---

