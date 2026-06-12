---
title: "An error during updating and installing"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by Obscene on 2007-07-21
Hello everybody
I'm a new beginner ubuntu user wish for help
there's an error message shown every installing (updates and programs)
here's the text shown in error box :
E: gnome-media: subprocess post-installation script returned error exit status 1
E: sound-juicer: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured

Sorry for disturbing and plz stand on limited knowledge

---

### Post by upchucky on 2007-07-21
there are repositories that have packages and most packages need other "files", that is, they depend on other files to work, the application looks for those other files and when it cant find them it sends u an error. 

so.. u must be sure u are getting the packages and the "files" they depend on when the update happens.

if u do not have all the supported ubuntu repositories entered in your repository file then some packages will error.


google search for info on ubuntu repositories and how to add more repositories to your system, once u have all the repositories u need then u should not get those errors, unless u are trying to install unsupported packages, then you have to manually find all the dependencies the package needs.

---

### Post by Seisen on 2007-07-22
Try this in the terminal

```
sudo dpkg --configure -a 
sudo apt-get -f install
```

---

