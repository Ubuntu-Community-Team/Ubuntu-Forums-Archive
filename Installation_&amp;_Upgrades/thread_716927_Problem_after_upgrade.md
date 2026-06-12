---
title: "Problem after upgrade"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by undencem on 2008-03-06
After I upgraded from 7.04 to 7.10 ,my pc slowed down while booting and running processes.And before having the Ubuntu Login screen,I am facing KUBUNTU welcome screen.

Any help appreciated

---

### Post by prshah on 2008-03-06
Whoops looked like you upgraded to "K"unbuntu... what was your upgrade path? CD, Internet, etc?

Anyway to get back to Ubuntu familiar screens, switch to 1st virtual terminal (Ctrl+Alt+F1), login and give the commands:

sudo /etc/init.d/kdm stop
sudo /etc/init.d/gdm start

If it is OK, report back and I/others will tell you how to set it permanently.

btw, it would be better to get rid of KDE if you are not using it... in my personal experience, KDE and Gnome do not live well together.

Cheers,
PRShah

---

### Post by undencem on 2008-03-07
Firstly the kde stop and gnome start didnt work

Secondly  I uninstalled all the KDE by Synaptic and the system crashed.

then from the virtual screen (Ctrl+Alt+F1)  I made

sudo apt-get install kde

installed all the packages to recover the system and save my files .

Now I have a Ubuntu that has a KDE 3.5 desktop .Some files from Ubuntu are running and some arent.

Happily I saved my files but I have to install ubuntu or any other Linux again

---

### Post by prshah on 2008-03-07
Please give the exact error message you got when trying to stop kdm and start gdm.

Cheers,
PRShah

---

