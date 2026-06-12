---
title: "The easiest way to Fluxbox?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by becatlibra on 2008-10-15
Let me say I am currently running fluxbox on ubuntu without a problem.  What I am interested in is reducing the footprint overall.

fluxbuntu seems like the project that couldn't unfortunately.

I want to be able to use the ubuntu repos but have fluxbox as my default without needing to have gnome installed at all.

My thought was maybe using the server install and adding fluxbox on that but I don't need/want any server apps really.

What I would like is to have a commandline install of ubuntu and then add fluxbox, et al. to it

Any ideas/opinions?

Thanks

Benjamin

---

### Post by simtaalo on 2008-10-15
check out crunchbang [http://crunchbang.org/projects/linux/](http://crunchbang.org/projects/linux/)

---

### Post by kerry_s on 2008-10-15
> **becatlibra said:**
> Let me say I am currently running fluxbox on ubuntu without a problem.  What I am interested in is reducing the footprint overall.

fluxbuntu seems like the project that couldn't unfortunately.

I want to be able to use the ubuntu repos but have fluxbox as my default without needing to have gnome installed at all.

My thought was maybe using the server install and adding fluxbox on that but I don't need/want any server apps really.

What I would like is to have a commandline install of ubuntu and then add fluxbox, et al. to it

Any ideas/opinions?

Thanks

Benjamin


yeah, just grab the alternate cd, do the command line install and build up from there. just to let you know there's no way around some of the gnome stuff, especially in ubuntu where they tie everything together, you'll get some, but how much depends on what you install.

sudo apt-get install xorg fluxbox etc...
then
startx

---

### Post by RedSquirrel on 2008-10-15
becatlibra,

For your command-line system, have a look at the [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD").


**Edit:** (I forgot to mention...)
You can avoid installing Gnome-related programs/libraries if you look very closely at the dependencies of every application before you install it.

---

### Post by snowpine on 2008-10-16
I actually learned a lot from Fluxbuntu, but I've moved on. I think a minimal install from the command line is what you're looking for. Here's a good tutorial: [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones) 
It uses IceWm but you can easily substitute Fluxbox instead. 

Lately I've been preferring Openbox to Fluxbox. Crunchbang is a good example of what's possible with Ubuntu 8.04+Openbox.

---

### Post by gjoellee on 2008-10-16
I don't know which text editor you have in Fluxbox but it is "gedit" in GNOME and "kwriter" in KDE.
```
 <your text editor> /etc/apt/sources.list
```

now add those lines to the file and save:
```

deb http://ppa.launchpad.net/fta/ubuntu hardy main 

```

I am not sure if this will install GNOME, but you will be able to use Hardy Herons "main" repo

---

