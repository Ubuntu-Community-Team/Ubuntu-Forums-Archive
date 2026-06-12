---
title: "init: timeout opening/writing control channel /dev/initctl"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Spuds on 2007-04-27
Brand new install of Ubuntu.  

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

Now I have:

init: timeout opening/writing control channel /dev/initctl

When I try to reboot to get the new kernel.  Can't shut down, can't init 6.

Tried reinstall of sysvinit, no success.

deb [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) edgy-seveas all
and 
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

are the only two lines in my sources.list that AREN'T ubuntu.com repos.

This *IS* a hosted server to which I do not have access.  One thing I found as soon as I got into the server was that it had only a single line in the sources.list and that was a debian repository.

Any help to correct this problem would be greatly appreciated.

---

### Post by Spuds on 2007-04-27
I wanted to also mention that I removed the debian line... but no telling what THEY did before I got to the machine.

Spuds

---

### Post by Dieter@be on 2008-03-09
Try 'reboot -f'

[http://thenthdoctor.blogspot.com/2007/03/timeout-openingwriting-control-channel.html](http://thenthdoctor.blogspot.com/2007/03/timeout-openingwriting-control-channel.html)

---

