---
title: "Unable to install ubuntu-desktop"
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by arshadparvez on 2011-07-20
AoA;

With repeated install/uninstall, I have somehow deleted all desktop environments except LXDE (which came when I was trying lubuntu) and openbox, which just got in from nowhere. Now I do not have gnome, ubuntu or unity options at login screen - only LXDE and openbox.

I read few tutorials and tried to install ubuntu-desktop. It doesn't install and after a long list of uninstallable dependencies; informs about "Broken packages". I know that my system is rather broken.

Can someone help me plz? I am pasting the error msg below:

aa@ubuntu:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-desktop : Depends: baobab but it is not going to be installed
                  Depends: evince but it is not going to be installed
                  Depends: gnome-screenshot but it is not going to be installed
                  Depends: gnome-search-tool but it is not going to be installed
                  Depends: gnome-session but it is not going to be installed
                  Depends: gnome-system-log but it is not going to be installed
                  Depends: gnome-terminal but it is not going to be installed
                  Depends: metacity but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Recommends: brasero but it is not going to be installed
                  Recommends: empathy but it is not going to be installed
                  Recommends: evolution but it is not going to be installed
                  Recommends: evolution-exchange but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
E: Broken packages

----------------------

What can I do to get gnome-2 working? ... even unity will do

regards

Arshad

---

### Post by mikewhatever on 2011-07-20
To fix a broken package, try **sudo apt-get install -f**.

PS: OpenBox is the default window manager in LXDE. ;)

---

### Post by Bucky Ball on 2011-07-20
Tried:

```
sudo apt-get update
sudo apt-get upgrade
```

?

---

