---
title: "how to redo dist-upgrade?"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by supenguin on 2005-10-21
Yesterday I tried doing a dist-upgrade from Hoary to Breezy using the Breezy CD. I commented out all the hoary repositories in /etc/apt/sources.list and did apt-cdrom add (I think that was the command) to add the Breezy CD as a repository. I then did an "apt-get update" followed by "apt-get dist-upgrade". Problem was the first time I did this it was from gnome-terminal, and it locked my system. I rebooted and trying running the same thing from the command line, but the dist-upgrade died when it hit gnome-terminal. I think either the gnome-terminal on my computer or CD was corrupted.

Afterward, I couldn't get dist-upgrade to continue. I tried to do "apt-get -f install" and then manually installed all the bits and pieces of gnome from CD with dpkg -i g/*gnome*/*.deb on the packages on the CD. I have a working system again, but this seems to have missed a lot of packages, xscreensaver and gaim for example. Also dist-upgrade says its all upgraded. 

So... My question finally... Is there anyway I can tell dist-upgrade to install everything that is considered the "base" Ubuntu system? In other words, have it install all the packages it would have installed if I did a clean install from the CD?

---

### Post by seldenthuis on 2005-10-21
'sudo apt-get install ubuntu-base ubuntu-desktop' should give you all the 'base' packages. Gaim you will probably have to install manually.

---

### Post by supenguin on 2005-10-21
Thanks! That seems to have done the trick. I suspect that gaim was included in the ubuntu-desktop meta-package, but I can't tell now since I installed it manually already.

The only problem now is the volume control applet is invisible. I've tried re-adding it several times, and didn't think it added until I accidentally clicked on it one time. Any ideas? Is there some other package I need to install?

---

### Post by vayu on 2005-11-03
[QUOTE=supenguin]The only problem now is the volume control applet is invisible. I've tried re-adding it several times, and didn't think it added until I accidentally clicked on it one time. Any ideas? Is there some other package I need to install?[/QUOTE]

After installing Breezy, I had a volume control that was just a single pixel vertical line.  You could only see it when the panel was set to transparent. It didn't work.  If I added a new volume control I would get another vertical line.  I couldn't access it to delete it.  It fixed itself after I added all the gstreamer and multimedia stuff in the ubuntu guide.

---

