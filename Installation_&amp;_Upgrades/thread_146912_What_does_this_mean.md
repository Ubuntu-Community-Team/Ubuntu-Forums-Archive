---
title: "What does this mean?"
date: 2006-03-19
forum: Installation &amp; Upgrades
---

### Post by cab1024 on 2006-03-19
I'm noticed these errors since trying to use a recent Easy Ubuntu. The errors show up when I launch Synaptic Package Manager. I think they are preventing Easy Ubuntu from actually working and mybe other packages from being installed properly.

> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)


Anyone know how I can fix this?

I just installed Breezy Badger from scratch, ran Easy Ubuntu, then ran the Softaware Update. (I did it Install, Update, Easy Ubuntu prior but that didn't work either.) None of the Easy Ubuntu packages installed.

Thanks for the help.

---

### Post by dermotti on 2006-03-19
I would disable the cd-rom respositories in synaptic and make sure the internet ones are enabled....

---

### Post by Xecuter on 2006-03-19
Try **sudo apt-get update** and then run Synaptic.

If the problem is still there you should change the source.list.

---

### Post by cab1024 on 2006-03-19
[QUOTE=dermotti]I would disable the cd-rom respositories in synaptic and make sure the internet ones are enabled....[/QUOTE]
Perfect. I think that worked. Makes sense once you understand what it is the error is saying.

---

