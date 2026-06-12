---
title: "broken package 'compholio'  - 14.04 ubuntu 64, not sure how to solve"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by xigen on 2014-08-26
I get the red circle with a white line through it.  The text says:  

An error occured, please run package manager from the right click menu of apt-get in a terminal to see what is wrong.
The error message was: 'unknown error': <'class key error'>, the cache has no package named wine-compholio-i386.  Unmet dependencies.

A search gave me several apt-get commands to try to remedy the issue:
without luck..

```
  123  sudo apt-get update
  124  sudo apt-get -f install
  125  apt-get
  126  apt-get check
  127  sudo apt-get check
  128  sudo apt-get install -f 
  129  sudo apt-get autoremove linux-image-generic
  130  sudo apt-get update
  131  sudo apt-get autoclean
  132  sudo apt-get clean
  133  sudo apt-get autoremove
  134  sudo killall synaptic
  135  sudo rm /var/lib/apt/lists/* -vf 
  136  sudo apt-get update
  137  sudo apt-get clean
  138  sudo apt-get autoclean 
  139  sudo apt-get autoremove
  140  apt-get -f install
  141  sudo apt-get -f install
  142  grep Broken /var/log/dist-upgrade/apt.log
  143  sudo apt-get purge netflix-desktop:i386
  144  sudo apt-get autoremove
  145  sudo apt-get install netflix-desktop
```

there is a bug report:
[https://bugs.launchpad.net/pipelight/+bug/1318321](https://bugs.launchpad.net/pipelight/+bug/1318321)

Any suggestions?

---

### Post by witchbutter on 2014-08-26
I saw this error as well, and I think it's just that there was a broken dependency at one point that needed updating, but that in order to fix it you need to use autoremove to remove the old dependency.

All I did for this was:
sudo apt-get autoremove
sudo apt-get dist-upgrade

I'm assuming you have the pipelight ppa installed, which is where I got this package.  Also be aware that dist-upgrade will upgrade your kernel version if that's an issue.

---

