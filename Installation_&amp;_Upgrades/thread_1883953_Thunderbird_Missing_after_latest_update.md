---
title: "Thunderbird Missing after latest update"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by zubairw on 2011-11-20
So i have a unique problem. Everything was working great and then i installed the security update on 19th Nov. After that i cant find/run thunderbird. There is a check email on the unity dash but nothing happens. i tried installing it again(did not un-install it, it just disappeared) but it says dependencies not installed. Exact syntax is:

The following packages have unmet dependencies:

thunderbird: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
             Depends: libnotify1 (>= 0.5.0) but it is not going to be installed
             Depends: libnotify1-gtk2.10 but it is not going to be installed
             Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed

I am also attaching screen shots if they might help. I'm running Ubuntu 11.10 64Bit. I am a bit of a noob on Linux so if this is some silly thing then sorry in advance.

Thanks

---

### Post by Frogs Hair on 2011-11-20
Try the following Commands.```
sudo apt-get autoremove

```

(Attempt to fix broken packages.)
```
sudo dpkg --configure -a 
```
Or 
```
sudo apt-get -f install
```


(Update and install)
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by zubairw on 2011-11-20
Ok solved the problem.
I had a separate ppa for Thunderbird in natty which was conflicting with the current one. Disabled it and problem solved.
Thanks for the help

---

