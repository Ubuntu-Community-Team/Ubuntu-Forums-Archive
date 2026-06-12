---
title: "Graphics Issues (Blinking Screen, 640x480 Resolution)"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by nioin3k on 2012-06-22
Hey guys, thanks for taking a look.

I think that there is a compatibility issue with my 8800gtx and ubuntu 12.04.

When I try to install, the screen blinks, and does not progress - so I install with nomodeset. If I boot without nomodeset after the installation, then ubuntu runs extremely slow, an action takes 20 seconds after clicking, etc.. so it's unusable.

Next I booted with nomodeset, and installed the latest nvidia drivers (259.59), but after installing them I was only able to choose 640x480 resolution, so I followed instructions from another thread and used:
```
sudo apt-get purge xserver-xorg*
sudo apt-get install xserver-xorg xserver-xorg-video-all
sudo reboot
```

This just set me back to the original problem with a blinking/blank screen that does not progress.

I would prefer to just do a fresh install if possible, with the latest drivers and no blinking or resolution issues.

All help would be appreciated. 

Thanks again.

Edit: I fixed it by reinstalling with password at login, in order to go into Ubuntu 2d, then used

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

Sorry for dumb post. Please delete me! Thanks.

---

### Post by dino99 on 2012-06-23
" Sorry for dumb post. Please delete me! Thanks. "

good to know you have solved your problem, but this thread is yours; and it should be a good idea to use the "Thread Tools" on top right corner to mark it as "SOLVED" ):P):P

---

