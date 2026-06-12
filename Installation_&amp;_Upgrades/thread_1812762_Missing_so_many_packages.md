---
title: "Missing so many packages"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Ibanezz on 2011-07-26
Why there are missing so many packages and how can I install them ?
here is the output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openssh-server' instead of 'ssh-server'
Package chromium-browser is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package vlc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Unable to locate package htop
E: Unable to locate package espeak-gui
E: Unable to locate package miredo
E: Unable to locate package terminator
E: Unable to locate package open-ssh
E: Unable to locate package gresistor
E: Unable to locate package abiword
E: Unable to locate package audacious
E: Unable to locate package audacity
E: Unable to locate package emesene
E: Package 'vlc' has no installation candidate
E: Unable to locate package recordmydesktop
E: Unable to locate package bluefish
E: Unable to locate package oggconvert
E: Unable to locate package soundconverter
E: Unable to locate package winff
E: Unable to locate package sysinfo
E: Unable to locate package build-essentials
E: Package 'chromium-browser' has no installation candidate

---

### Post by oldos2er on 2011-07-26
Run ```
kdesudo software-properties-kde
``` and make sure all the repositories you want are checked. Close and run ```
sudo apt-get update
```

---

