---
title: "Upgrade attempt gone horribly wrong, help!"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by Greeface on 2006-11-18
I was attempting to upgrade to Edgy, but I guess I had some important pakages locked or something.  It errored a bunch and the aborted.  Now I have a bunch of broken pages and unmet dependencies.  I can't really do anything in terms of installing/upgrading/removing packages.

I don't want to try restarting because xserver-xorg-core is one of the broken packages.

ANY help is appreciated, I'm stuck here and I don't know what to do.

Thanks

---

### Post by an.echte.trilingue on 2006-11-18
Are you using the graphical upgrader or apt-get dist-upgrade?

apt-get dist-upgrade can usually fix things like this, if it does not it well tell you where the hang-ups are (aka, which packages you need to uninstall by hand and re-install after the upgrade).

---

### Post by Greeface on 2006-11-18
I originally started the upgrade using the graphical one until it screwed up.  I couldn't fix it using apt-get, though.  It wants me to fix broken packages, but when I try to it says there's dependency problems.  It won't work through synaptic either.

---

### Post by Greeface on 2006-11-21
I eventually got it working after backing up and completely reinstalling.

Thanks

---

