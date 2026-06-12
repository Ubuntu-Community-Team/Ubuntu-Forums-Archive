---
title: "Gutsy upgrade broken - gonme-themes and ubuntu-desktop"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by analyzer123 on 2007-10-22
Hello all,
I am posting my problem again. 

I tried upgrading from feisty to gutsy today, with disastrous results. I used the update-manager from the gnome administration and said upgrade.

1) all files were downloaded correctly
2) installation went till about 60%
3) after this, it started giving dependency errors, saying certain modules could not be installed, which included:
gnome-themes
ubuntu-desktop

There were 2-3 popups in the middle, with the same kind of errors, but finally the upgrade just aborted and said to check the logs, and report a bug under "update-manager"

The final error is in:
ImportError: No module named apport
Could not import module, is a package upgrade in progress? Error: /var/lib/python-support/python2.5/gtk-2.0/gobject/_gobject.so: undefined symbol: g_timeout_add_seconds_full

I have truncated the log files and have attached it to this post. 

Now I am left with an unstable, unusable system. If I boot it, gnome doesnt start up. I can login thru the text console, but essentially cant do anything. The NIC is not working, X is not working. I put in the alternate install CD, mounted it and ran
gksu "sh /..../cdromupgrade", but it gives an error saying "gtk...cannot start x server"... the X is running on console 7, but its just a blank screen!

System: dell e1405, intel integrated graphics, dell 1390 wireless

Please help. How do I upgrade to gutsy? Clean install?

Secondly, is there some known problem with gutsy and Intel integrated grpahics card (like 945GM). feisty+beryl worked perfectly on my laptop, but I read some posts saying the performance is too sluggish in gutsy.

---

### Post by pdlethbridge on 2007-10-22
I tried for the second time to upgrade to gutsy, both were disasters. I'm now back to feisty.

---

### Post by analyzer123 on 2007-10-22
did you try with the CD the second time? if so how do we change the sources file to read only from CD? my network interface is not working anymore :((

---

### Post by TDogg310 on 2007-10-22
I experienced the very same problem when I tried to upgrade to Gutsy from Feisty on my Vista/Ubuntu dual boot laptop using update manager.  When I tried this the first time, I couldn't even get past to the downloading part because of dependency errors.  I did a search of the error message,  leading me to an error posting in which the culprit was decided to be Ubuntu Studio.  I had been using the theme, graphics, and sounds of Ubuntu Studio, and tried uninstalling them.  Once they were all gone, I was able to proceed with the upgrade.  Everything downloaded fine but when it got to configure the install I noticed that it was showing problems with Gnome in the terminal, specifically Gnome-perl I think.  I also saw that it was frequently showing a Glib version mismatch error.  It popped up with a message stating that ubuntu-desktop could not be installed, and I knew I was in trouble.  This was followed by the installation being aborting. At least some of Gnome ought to be working, since I am shown the nVidia screen when I try to boot up to Gutsy, followed by a cursor that idly rotates.  I have already made an alternate install disc, which is nearly useless as far as I know since I can't boot to Feisty and I get the error "gtk cannot start X-server" when I try to run gksu "sh /cdrom/cdromupgrade . 

Any help would be appreciated, but I do have all important files backed up.  I had been experiencing stability issues with Feisty in that it would freeze after being in use for about 3 hours, and I was hoping that Gutsy would fix them.   I have an HP DV6000t with an Intel Core 2 Duo (Centrino Duo) and an nVidia Go 7400.

---

### Post by motin on 2007-11-06
Just a thought - maybe you should make sure that the meta packages are available to start with?
```

sudo aptitude -y install gnome-themes
sudo aptitude -y install ubuntu-desktop

```
Sometimes instructions for Compiz and the likes says you should remove them...

---

