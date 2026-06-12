---
title: "Openoffice.org2 refuses to install"
date: 2005-10-15
forum: Installation &amp; Upgrades
---

### Post by turni on 2005-10-15
I just installed Breezy and for some reason Openoffice.org2 failed to install and comes up as broken, while everything else (which does not have it as a dependancy) seems to have worked. I have tried apt-get/synaptic to try and reinstall. 

apt-get outputs a whole load of things along the lines of *"openoffice.org2: Depends: openoffice.org2-core (> 1.9.129) but it is not going to be installed"* for each of the openoffice packages. 

Synaptic outputs *"E: /var/cache/apt/archives/openoffice.org2-core_1.9.129-0.1ubuntu4_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice2/program/libsb680li.so')"* and the same for writer, but none of the other packages. 

Does anyone have any ideas of how I can deal with this? 

Thanks,

Sam

---

### Post by manicka on 2005-10-15
Have you tried completely uninstalling the broken packages in synaptic, then reinstalling?

---

### Post by hollows2 on 2005-10-15
I've always had problems with Office 2 packages from Ubuntu. In the end I downloaded the rpm's from the open office web site and installed using alien -iv * rpm.

You'll need to also load the desktop menu deb package using dpkg --install *deb. this is in a sub directory of the untarred files

This seems to work OK.

Steve

P.S I actually managed to load the Office packages using synaptic but I had problems with the Office packages displaying graphs in calc - the official version from the Office site had no such problems

---

### Post by DisposableMike on 2005-10-20
This exact same thing happened to me. I fixed the problem by doing an "apt-get clean" which removed the deb file from my /var/apt/cache location. This forced it to re-download it and this time it installed without problems. (install again via "apt-get -f install". Unfortunately, some other work had to be done to get internet connection and all that.

---

