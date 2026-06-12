---
title: "Jaunty and Partial Upgrades?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cfogelberg on 2009-04-08
Hello,

I'm new to using Ubuntu and I've just installed the Jaunty beta on my Dell XPS M1330. I've run all of the updates, but three of them won't install and so I've only done a "partial update":
* ekiga
* indicator-applet
* indicator-messages
All won't install. Is that because they are still in development? If so, when should I expect them to be upgradeable? Should I worry about them not being installed for now?

Thanks,
Christo

---

### Post by durand on 2009-04-08
You should post this in the jaunty forums. ([http://ubuntuforums.org/forumdisplay.php?f=352](http://ubuntuforums.org/forumdisplay.php?f=352)) I think partial updates means that the dependencies for the update aren't ready yet so you will need to wait until they've been updated as well.

---

### Post by cfogelberg on 2009-04-08
Hi,

Thanks for your quick response. I did some more searching and it seems I could (wisely or unwisely) force the updates through the Synaptic Package Manager or sudo apt-get full-upgrade, which I did (the former), and I didn't get any error messages/warnings that way

There were quite large version number differences between the old version and the new/upgraded version so would that have caused it? All three also needed some library upgrades.

Anyway, if I have any problems like this again I'll ask in the Jaunty forum. Thanks again,

Christo

---

### Post by durand on 2009-04-08
Forcing the updates usually does little damage however it may not always work and it's not a clean solution either.

---

### Post by Hospadar on 2009-04-08
Yes, whenever dependancies are added or removed, or packages change names, etc, you'll need to do a "sudo apt-get dist-upgrade" to get the included packages.  Usually new kernel versions and the things that depend on them are really the only thing that falls into that category, but since jaunty is still being very actively updated you'll see more than usual fall under the "dist-upgrade" umbrella.

Generally it's totally safe to do these upgrades, as I said, most often it's just a new kernel version or renamed dependancies

---

