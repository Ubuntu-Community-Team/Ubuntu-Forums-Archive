---
title: "Super OS upgrade?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by m005k on 2010-04-30
Can I upgrade Super OS to 10.4 or should I wait until there is a specific Super OS 10.4 made?

Mike

---

### Post by dino99 on 2010-04-30
as super os is a ubuntu mod, you should upgrade without troubles i guess. As always clean your distro first: autoremove, install -f

then uncheck all third party repo and ppa too if you have, then i dont know if you can dist-upgrade directly (maybe not but no sure), 

in that case open the repo list:

sudo gedit /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed multiverse restricted universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports multiverse restricted universe main
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free

then update and upgrade

---

