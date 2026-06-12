---
title: "Circumventing apt-get with source code?"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by MichaelBaum on 2007-12-05
I haven't been able to come up with a search pattern for these forums (fora??) that quite expresses this, so I apologize if this is an Already Answered Question.

I need to install a couple of major programs on my kubuntu 7.10 system by compiling them from the sources. They include apache 2.x, mysql and php5. Actually, I probably don't need to build all of those from scratch, but certainly the apache for various reasons not relevant here.

The question is, once I've done that, how can I inform the package managers like adept or synaptic or dpkg that 1) the programs actually _are_ installed but 2) they shouldn't try to maintain them?

I need to do (1), because other programs managed by the package system may depend on the programs I've built, and the manager will refuse to install these new programs without satisfying the dependency -- which would undo my work. I need (2) because if I successfully tell the package system that these programs are installed, i don't wnat them to try to install upgrades to, e.g., apache that would break my customized settings.

How do I do this?

TIA, maab

---

### Post by monktbd on 2007-12-05
you could try to use [checkinstall]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=checkinstall&searchon=names&subword=1&version=gutsy&release=all") instead of make install which builds a deb package for you you can install.

---

### Post by mozetti on 2007-12-05
Check the aptitude man pages (or conversely, use the Synaptic GUI) - there are options for not monitoring programs and/or locking the current version.

---

