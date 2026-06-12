---
title: "failed gutsy to hardy heron upgrade"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by bruble on 2008-04-30
Help
Update manager failed when trying to install/configure apache2-mpm-prefork.
I tried to use sudo ifup wlan0 to get a web connection but sudo cannot be resolved for myuser.
I am unable to login as root.
I ran dpkg --configure -a in gnome failsafe mode but this too failed with apache2-mpm-prefork.
can run apt commands and some other commands.
All pakages have been downloaded.
Update manager does not permit me to deselect apache2-mpm-prefork

What can I do and how. Any help appreciated.
Thanks
========================================
Have droped into Grup and run apt-get install -f as root. 
This suggested I also run apt-get autoremove
perhaps foolishly I decided to do so
174 still to upgrade so it seems
still not able to use sudo even after tryng to adduser to adm admin
Tried running update manager again apache2-mpm-prefork has dissapeared but was unable to get update manager to install the rest of Hardy Heron
====================================

---

### Post by bruble on 2008-04-30
have now tried to manually upgrade by going into grub and root.
used commands apt-get update host of errors
next apt-get upgrade and it is on its way

---

### Post by bruble on 2008-04-30
sudo can be fixed by editing the /etc/hosts file to remove the domain name that will appear appended to the name of your computer.
eg 127.0.0.1 mymachine.mydomain needs to be changed to
127.0.01 mymachine

---

