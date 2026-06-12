---
title: "Help - KDE uninstalled!!!"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by infoseeker on 2010-02-14
This morning I did the regular 'sudo apt-get update' and 'sudo apt-get upgrade' and thereafter 'sudo apt-get dist-upgrade' after which I was left with a dysfunctional KDE.  Last time this happened to me I managed to get my system up and running again by 'sudo apt-get install kubuntu-desktop'.  This time my problem is different because I get:
```
Reading package lists...
Building dependency tree...
Reading state information...
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kubuntu-desktop: Depends: kdebase-workspace-bin but it is not going to be installed
                   Depends: language-selector-qt but it is not going to be installed
                   Depends: plasma-desktop but it is not going to be installed
                   Depends: software-properties-kde but it is not going to be installed
                   Recommends: apport-kde but it is not going to be installed
                   Recommends: apturl-kde but it is not going to be installed
                   Recommends: install-package but it is not going to be installed
                   Recommends: jockey-kde but it is not going to be installed
                   Recommends: kpackagekit but it is not going to be installed
                   Recommends: kubuntu-firefox-installer but it is not going to be installed
                   Recommends: kubuntu-notification-helper but it is not going to be installed
                   Recommends: plasma-widget-facebook but it is not going to be installed
                   Recommends: plasma-widget-googlecalendar but it is not going to be installed
                   Recommends: printer-applet but it is not going to be installed
                   Recommends: system-config-printer-kde but it is not going to be installed
                   Recommends: usb-creator-kde but it is not going to be installed
                   Recommends: userconfig but it is not going to be installed

```
Any ideas?



EDIT:
Found this---> (wish me luck)

[http://www.linuxforums.org/forum/debian-linux-help/110983-unmet-dependencies.html](http://www.linuxforums.org/forum/debian-linux-help/110983-unmet-dependencies.html)

---

### Post by ranch hand on 2010-02-14
Running "dist-upgrade" is not a good thing to do without checking very carefully.

I would see if you can install the depends listed in your out put from terminal.  I would use multi terminals or multi tabs so that you can keep the outputs.  You could copy them to a text editor also.

If that does not work you could try a different desktop environment but that sounds kind of desperate.

---

### Post by koso on 2010-02-14
Fixed verision of kdebase is already being built. Then you should install all uninstalled packages

---

### Post by cookiecruncher on 2010-02-14
Its me again ;)

To give me a functional desktop I issued 'sudo apt-get install lubuntu-desktop'  and has left me with a gorgeous LXDE desktop :)

Fortunately KDM was still functional, and all it took was about 100MB download.

I'll give it a few days and then attempt to get the KDE desktop up and running again.  In the meantime I'll enjoy LXDE.

---

### Post by ranch hand on 2010-02-14
I have Lubuntu 10.04 on a pair of partitions and it is looking very nice.  The entire OS is using only 6Gb total and that includes gimp, gthumb, gparted, rhythmbox and a lot of music that I added on.

I am thinking of installing it on an old HP pavilion xt993 that is currently running Ubuntu 8.10.  I think it will be easy on old hardware when released.  Really looking good.

I also really like pcmanfm.  A little bit to learn to use it but it is fast.

EDIT

The music I added is 3Gb of that 6Gb total.  Remove gimp and you have a very functional but tiny OS.

---

