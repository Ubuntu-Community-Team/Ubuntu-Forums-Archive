---
title: "Having issues installing kamoso (or anything else, it seems)..."
date: 2018-05-07
forum: Installation &amp; Upgrades
---

### Post by robertmayes21 on 2018-05-07
Hi, I'm really new to linux and ubuntu.  I've been trying to install kamoso, and other programs, and update, but I keep getting errors:

sudo apt-get install kamoso
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 kamoso : Depends: qml-module-org-kde-purpose but it is not going to be installed
          Depends: libkf5declarative5 (>= 5.0.0) but it is not going to be installed
          Depends: libqt5glib-2.0-0 (>= 1.2.0) but it is not going to be installed
          Depends: libqt5gstreamer-1.0-0 (>= 1.2.0) but it is not going to be installed
          Depends: libqt5gstreamerquick-1.0-0 (>= 1.2.0) but it is not going to be installed
 linux-image-extra-4.10.0-37-generic : Depends: linux-image-4.10.0-37-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.10.0-37-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

so then, I try to follow the instructions:

apt --fix-broken install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

...Can anyone help me out here?  I would really appreciate it.

Thanks!

---

### Post by cruzer001 on 2018-05-07
Hello

First close all running programs except your browser, then run
```
sudo apt -f install
```
-f is short for fix-broken and sudo gives you permission

If you get errors, please post the output.

PS
Also post
```

lsb_release -a && uname -r && echo $XDG_SESSION_TYPE
```

---

### Post by ubfan1 on 2018-05-08
After you installed Ubuntu, in a terminal, did you first run 
```
sudo apt-get update 
``` 
 before trying to install anything else?
Then upgrade everything installed with
```
sudo apt-get dist-upgrade
```
Then you can start installing new packages.

---

