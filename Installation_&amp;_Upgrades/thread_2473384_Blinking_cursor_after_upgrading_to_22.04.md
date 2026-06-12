---
title: "Blinking cursor after upgrading to 22.04"
date: 2022-04-02
forum: Installation &amp; Upgrades
---

### Post by a4c8 on 2022-04-02
In the beginning I checked with the live usb if 22.04 still runs on my machine and everything looked fine.

I started the upgrade using ```
sudo do-release-upgrade -d
``` ending up in a blinking cursor.
Pressing ctrl-alt-del after a while lead to a reboot with the exact same state.

I can login after pressing ctrl-alt-f1. When I ran ```
sudo apt-get update
``` I got a python error saying, that a module wasn't found. I therefore compiled the latest python 3.10.3 vs. my version 3.8.x, set a symlink and the error went away.

However, if I ```
sudo apt-get upgrade
``` (see attached file) I get a bunch of dependency problems, some still related to python not having the right version, although ```
python3 --version
``` states 3.10.3

I tried running ```
sudo apt --fix-broken install
``` (see attached file) but similar errors occured.

How would I fix this? Is there maybe a hidden option to upgrade again using the installed from the live media? I only found an option to reinstall losing all my installed programs etc.

---

