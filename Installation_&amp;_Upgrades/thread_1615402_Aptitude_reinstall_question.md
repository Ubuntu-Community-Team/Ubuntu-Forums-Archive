---
title: "Aptitude reinstall question?"
date: 2010-11-06
forum: Installation &amp; Upgrades
---

### Post by mabo1 on 2010-11-06
I have been having problems with my ubuntu 10.10 install, I have completed a fresh reinstall 4 times, but I am still having problems.

I would like use aptitude to do a reinstall, so is it possible to force aptitude to reinstall all dependent packages as well.

example; sudo aptitude reinstall gnome-core, only reinstall this package, is their way I can force it reinstall all dependent packages.

Thanks

---

### Post by garvinrick4 on 2010-11-07
Here are a couple of nice post installation instructions for Ubuntu
[Main Page -]("http://ubuntuguide.org/wiki/Main_Page")
[my-guides.net]("http://www.my-guides.net/en/") 

Get your repositories installed in software sources first then:
```
sudo apt-get install ubuntu-restricted-extras aptitude gparted
``````
sudo aptitude update && sudo aptitude safe-upgrade
```The first command gets all your flash,codecs, java, aptitude,gparted and such installed:
The second update and upgrades and deletes unneeded packages
If you get dependency problems anytime try.
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
```

---

