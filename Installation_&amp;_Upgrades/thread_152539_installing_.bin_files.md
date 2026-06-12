---
title: "installing .bin files"
date: 2006-03-30
forum: Installation &amp; Upgrades
---

### Post by patanjali on 2006-03-30
I am a newbie, so forgive the silly question, but how do you install .bin files?
I have downloaded the .bin file for RealPlayer10 Gold, and can find it in the file system (it is labelled as "executable"), but I can't get it to install.  Double clicking it does nothing, and right clicking it just gives the option "open with", which is less than useful.  Sorry to be so thick.
Patanjali

---

### Post by Perfect Storm on 2006-03-30
If you're on breezy i386 you can do this:

```
sudo gedit /etc/apt/sources.list
```

add:

[b]## Penguin Liberation Front
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) breezy free non-free
[/b]

save and exit.

```
sudo apt-get update
sudo apt-get install realplay
```

---

