---
title: "cd on hdd"
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by rob7622 on 2005-08-01
i finally did it...i'm finally in a windows-free environment...thanks guys.

i have a quick question.  when i was in a windows world i had copied the contents of my windows installation cd to a folder on the hdd.  that way if there was a situation that required a file off the cd i could direct the os to the folder instead of having to have the cd  with me all the time.

i tried this with linux but it seems that when it asks for the hoarty cd i can't direct it anywhere else...i'm forced to load the cd.

is there anyway i could change the default location of the installation files so i'm not forced to put my hoarty cd in the drive whenever i'm update/installing from synaptic?

thanks

---

### Post by jasmuz on 2005-08-01
Sure, copy all your .deb files in the cd on to /var/cache/apt/archives
that should do it.

---

### Post by varunus on 2005-08-01
If you have broadband, you can also just disable the CD, since all packages on it are also on the internet and can be downloaded if they need to be reinstalled.  Just open up your /etc/apt/sources.list with "sudo gedit" and comment out the CDROM line.

---

