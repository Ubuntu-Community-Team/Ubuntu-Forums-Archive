---
title: "blank screen after installing/upgrading with ATI card"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2011-12-08
i just installed 11.10 on my new notebook, and decided to install the ATI restricted drivers. and then, before rebooting, did a apt-get update & upgrade.

at the end i coudn't get X to run.

[this]("http://phoronix.com/forums/showthread.php?26363-Ubuntu-10.10-fglrx-failure") solved it

```
sudo stop gdm
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
sudo apt-get install --reinstall xserver-xorg-core
sudo rm /etc/X11/xorg.conf
sudo rm -r /etc/ati/
```
note: i didn't have fglrx-modealiases in my repo, so i just ignored.
also, the apt-get --reinstalls are really needed. you see messages about broken link in /etc/defaults or something being fixed. (i use aptitude instead of apt-get, and it lacks --reinstall)

note2: don't have to rm xorg.conf. just change driver to "vesa"

---

### Post by gcbzzzz on 2011-12-08
shouted vitory too soon.

this restore the vesa mode alright.

but the problem with fglrx was not simply that i installed it before the post-install update. jockey has no lucky updating it.

---

