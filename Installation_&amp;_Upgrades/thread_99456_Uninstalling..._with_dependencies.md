---
title: "Uninstalling... with dependencies"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by Ruskie on 2005-12-05
A question about uninstalling...
We all fancy (I suppose) the wonderful mechanism of dependencies that the package-system has... This way if I want to install, let's say, an Email application it's enough to select its package for a package manager to find, select, show me, download and install the bunch... And this is really great.
Also a clever move is the trick "ubuntu-desktop", a fake package that depends on every "standard" application for the desktop. Ok.

What I miss is something to reverse the process. If I install for example a 3d video game, it is very likely that it requires 3-4 libraries often big. No problem to install them. The problem arise if, a couple of month ago I decide to uninstall the package. I can well uninstall it, but what happens with all the dangling (unused thus space-wasting) libraries that remain there?
Write them down by hand for each installation is of course not an option... Also because some of them may in the meantime have become required for other applications installed more recently.
So, it seems to me that there is no way to smartly and safely remove unused library or packages... That is, packages that more than a real application provide services that nobody uses anymore...

Or am I (hopefully) wrong? In that case, how do I recognize (and then uninstall) "orphan" libraries?

Thank you
Marco

---

### Post by Qrk on 2005-12-05
Deborphan, with gtkorphan is a graphical app that will find orphaned libraries and uninstall them. I believe its in the repositories.

---

### Post by bwog on 2005-12-05
You can use Synaptic for that (system menu, administration, Synaptic). Just get familiar with the menu options and it will work out fine.

---

### Post by Ruskie on 2005-12-07
[QUOTE=bwog]You can use Synaptic for that (system menu, administration, Synaptic). Just get familiar with the menu options and it will work out fine.[/QUOTE]

Uhm... I do use Synpatic to install packages... But I don't know how can I tell it to find orphans... I know how to find obsolete packages, but it's not quite the same... How do you do that?

Also, I noticed that Synaptic regards as "local installed or obsolete" (if I remember well) the package libdvdcss2 installed by libdvdread3, which is not obsolete at all since you need it to play DVD-video...

---

### Post by Ruskie on 2005-12-13
[QUOTE=bwog]You can use Synaptic for that (system menu, administration, Synaptic). Just get familiar with the menu options and it will work out fine.[/QUOTE]

I managed to get Synaptic (and deborphan) to work and find orphaned libraries, but it's not quite what I wanted.

For example, having uninstalled America's Army, it does not recognize that gcc-3.3-base and libstdc++5 which I installed because required by it, and for which there aren't other dependencies because I didn't install anything else, are orphans.
Moreover, it regards as orphan the w32codecs package, while Kaffeine use it to play divx...
So, all in all, it is not 100% trustworthy, is it?

Thanks
Marco

---

