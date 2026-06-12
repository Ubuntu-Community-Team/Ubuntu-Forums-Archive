---
title: "update manager error"
date: 2011-08-06
forum: Installation &amp; Upgrades
---

### Post by orebob08 on 2011-08-06
my upgrade manager is not working it's giving me an error message after i am connected to the INTERNET

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.'

---

### Post by Rubi1200 on 2011-08-07
Hi and welcome to the forums :-)

Open a terminal with Ctrl+Alt+T and run the following commands (best just to copy and paste to avoid errors):
```

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes any corrupted package lists, the second one updates them.

---

### Post by jusis on 2011-08-18
thank you so much rubi1200!! it helped me solve the same problem right on the spot!
enjoy your summer! :)

---

