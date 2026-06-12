---
title: "problem with graphical interface"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by szymon_g on 2007-02-24
hi.
i've got a problem- i hate gnome ;-> but seriously: i wish i could make system withaut unnecessary programs (i.e- many from 'standard' ubuntu), if possible- delate all 'graphical' programs (e.g. OO, gdm, Xorg) and customise my ubuntu almost from scratch :-). i know- i could install 'command-line system' using ubuntu-alternate cd, but, unfortunatelly, i have some problems with my wi-fi card (intel ipw3945abg)- system doesn't see my card (i.e. iwconfig returns 'no wireless extension' on my all cards - eth0, eht1).
i used this way 

[http://forum.ubuntu.pl/viewtopic.php?t=17093](http://forum.ubuntu.pl/viewtopic.php?t=17093)

to delete gnome, but still alot of programms remaind... i also used a 'ubuntu pro 6.12' (polish command-line version of ubuntu EE), but there is still this problem :-/.

have a nice day/night :-)
szymon

---

### Post by NosLycn on 2007-02-24
I have the same annoying wireless card.  If you have access to a wired net connection, you should be able to get your wireless working by installing the restricted-modules.  After that, it just found the card for me.  Then, I just made sure that /etc/network/interfaces had some info for the card:

> 
iface eth1 inet dhcp
wireless-essid sunaco
wireless-key s:keyek

auto eth1


That's not the real wireless key, but you get the idea.  Then, I run a /etc/init.d/networking restart and it works.  You might need to reboot your computer entirely, but it should work using this method.

Best of luck.

---

### Post by szymon_g on 2007-02-25
thank you for answer :-)
btw, if i havent wired connection, it will be ok if i will download linux-restricted-image somewhere on my windows' partition, install command-line system, mount windows' part. and install via dpkg -i name ?
by 
szymon

---

### Post by NosLycn on 2007-02-26
It should work that way, yes.  The restricted bit is where they have the modules for the wireless adapter.  So long as you can get it working with a standard (graphical) install, you can get it working without the graphical.

---

