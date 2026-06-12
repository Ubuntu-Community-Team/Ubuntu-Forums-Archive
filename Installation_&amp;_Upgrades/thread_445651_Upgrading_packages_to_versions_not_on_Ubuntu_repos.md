---
title: "Upgrading packages to versions not on Ubuntu repositories"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by chasta on 2007-05-16
Hi,
[I'm a newbie to Ubuntu, so please forgive me if the following questions have an obvious answer. I certainly tried but have found no obvious answers.]

How do I update a package to a version not yet available from Ubuntu's repositories for my dist version (I've got all the relevant apt sources for my dist version enabled) ?

For instance, I want to upgrade ntfs-3g to the latest version (for better Vista inter-op) - and Feisty (which I'm using) still does not have it (Gutsy does) - how do I do that (safely...) ?

Secondly, what do I do in a case where no Ubuntu version sports the version I need? Am I correct to say that in such case I don't really have a choice but manual installation? (unless I find some 'foreign' apt repository that has the package?)

If I have to manually install, is there a good way to prevent collisions with apt's view of the system except for installing on a different prefix?

---

### Post by renzokuken on 2007-05-16
depends on the package, in some cases you may be able to find a current .deb file with google.

otherwise, it is usually a case of waiting for the repos to be updated or compiling from source. compiling from source is not as tricky as it may sound.

---

### Post by chasta on 2007-05-16
Thanks!

If I install from source a package which I hope in the future to get a .deb for (hopefully from the official repositories), what would be the best practices? E.g. I want to be able to easily remove the from-source installation and install via apt when a package is available.

Is installing in a different prefix my best choice in this case? It may involve some tinkering with configuration files, which I would have to undo before I install the package from apt... Isn't there something smarter I can do?

Anyway, thanks again for your help!

---

### Post by renzokuken on 2007-05-17
you could use a piece of software called 'checkinstall'.  

by using this as the last command in compiling from source i believe it actually creates a .deb file and adds it to your apt-get list of installed software. hence the program you compiled from source will appear in synaptic and you can simply uninstall it from there.

so instead of using the traditional compile commands

```
./configure
make
sudo make install
```

you would install checkinstall (and build-essential) first and then run

```
./configure
make
sudo checkinstall
```

---

### Post by chasta on 2007-05-17
Sounds great! I'll be sure to check it out.

Thanks!

---

### Post by Skerit on 2008-07-23
What do you do when a deb made with checkinstall is conflicting with other packages? (Like drivers which are trying to overwrite this file: /lib/modules/2.6.24-19-generic/kernel/drivers/media/common/ir-common.ko)

---

