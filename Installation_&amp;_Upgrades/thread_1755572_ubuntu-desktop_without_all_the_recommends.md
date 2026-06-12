---
title: "ubuntu-desktop without all the recommends"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by StaticPhilly on 2011-05-11
hi,

ok a pet hate, installers installing software i have not asked to be installed, linux is about choice :/
so now thats out the way ;)

can anyone tell me if its possible for the ubuntu-desktop installation image no to install the recommends or is it only possible with server using no-install-recommends?

if its only possible with server, can anyone tell me if i can install the graphical boot screens on server?

thanks in any advice
Phil

---

### Post by BlouBlou on 2011-05-11
Sure, I think you just need to install gnome and gmd. You should change your kernel too, from server to generic.

I think it should work fine after a reboot.

---

### Post by oldfred on 2011-05-11
If you want a minimal install.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Not used it and not sure if you can just not install the defaults as part of the process and then just install what your want.

The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
sudo service gdm start

More info here:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

