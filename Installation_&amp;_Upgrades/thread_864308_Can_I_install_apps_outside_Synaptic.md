---
title: "Can I install apps outside Synaptic?"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by kwanbis on 2008-07-19
I decided to go full Linux after many trials (Crossover Office now supports lotus notes 7 just fine), but I remember that i read somewhere not to install, for example, FF if it was not from the synaptic manager.

So i was wondering, why is it that i shouldn't use a deb/sh file, to install apps in ubuntu?

What would be the problems?

Or can i go for example, download Tux Commander.deb, and install it?

---

### Post by JagDragon on 2008-07-19
synaptic and apt-get are just managers that give a better interface for .deb files. They allow you to browse, and give automated download and install of them. You can install .deb files very easily though:
```
sudo dpkg -i myapp.deb
```
apt-get and synaptic are just nicer, simpler, and faster to work with.

Also, some programs are source code which you have to build and install, but I recommend you stick with what is in the repositories, as what is in there will be high-quality, Ubuntu-tested programs.

---

### Post by mikewhatever on 2008-07-19
Firefox can be downloaded from it's home site and installed, if you can figure out how, but why would you need two? It makes one's life simpler to install from synaptic, since, presumably, packages are better tested for the version you use and the repositories is a trusted source, unlike some obscure web sites.

---

### Post by kwanbis on 2008-07-19
Thanks guys.

So its more a matter of simplicity then.

For example, i wanted to install Tux Commander, and there is none at the repository, so i donwloaded a .deb.

Also, i want to install Skype, and IIRC, there is none also on the repos.

So i can go ahead and install them, right?

---

### Post by JagDragon on 2008-07-19
You can ... You could also find replacement programs for them (possibly not skype), but just have a look around. Pidgin does IRC, so does Kopete...

---

### Post by kwanbis on 2008-07-19
Thanks guys, i'm hapily running skype/tux commander ;)

---

