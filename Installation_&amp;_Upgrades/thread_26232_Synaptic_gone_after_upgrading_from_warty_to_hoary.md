---
title: "Synaptic gone after upgrading from warty to hoary"
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by dan1928 on 2005-04-12
I've had warty for quite some time and just the other day tried to upgrade to hoary. Since I prefer using Synaptic, I updated all the repositories through synaptic from warty to hoary. I then tried to update, but many of the repositories were coming back with errors about reaching the servers. I then followed the instructions for upgrading via Apt.  Everything upgraded just fine through the consol, except that Synaptic seems to be now missing (not in any menu). I tried apt-get synaptic but that just gives me and invalid operation. Somewhat of a n00b here, so any help is much appreciated. By the way, the instructions I followed above are [here](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes). 
Thanks!
-Dan

---

### Post by blueplazma on 2005-04-12
You should ```
sudo apt-get install synaptic 
``` and then restart Gnome.  It should show up in your Administration menu.

---

### Post by dan1928 on 2005-04-14
thanks so much blueplazma! It's been awhile since I've been able to get back to this, but I got things fixed with your help. I have one other small related issue if it isn't too much trouble. When I open synaptic and it loads the reps, it complains about some. I un-enabled the ones with issues, but I was curious if there is a list somewhere of the proper default repositories for synaptic and hoary. Thanks again!
-Dan

---

### Post by dan1928 on 2005-04-14
I think I answered my own question. I found an ubuntu wikipage that shows the default repository list (sources.list) [here](http://www.ubuntulinux.org/wiki/GuideToHoary).

Thanks again...

---

### Post by speedman on 2005-04-14
[QUOTE=blueplazma]restart Gnome.  It should show up in your Administration menu.[/QUOTE]

Just an fyi ... there is no need to log out and back in again to get newly installed apps to appear in the gnome menus.  Just issue this command in a term and will kill the gnome panel, which will respawn automatically with the new app present:

killall gnome-panel


Regards,

SM

---

