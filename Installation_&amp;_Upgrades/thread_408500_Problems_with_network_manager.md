---
title: "Problems with network manager"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by sirclesam on 2007-04-13
I just got ubuntu installed on my laptop, and am trying to get the wireless internet to work.

I read about network manager and it seemed like it would do the job.

However im running in to problems with the install,  it doesn't create a makefile that is recongnized by make.  Instead it makes Makefile.am and Makefile.in.  Running make on either of these results in the same error.
line ## missing seperator

is this a problem with make?

This is my first attempt to install any new programs using ubuntu or anything besides windows.

---

### Post by Austin_KW on 2007-04-13
You can (download and) install the ubuntu network manager package using apt, no need to make it.
in a terminal```
  sudo apt-get install network-manager-gnome 
```

---

### Post by zvacet on 2007-04-14
```
sudo aptitude install network-manager-gnome
```

Just in case if there is some dependencies to download.

---

