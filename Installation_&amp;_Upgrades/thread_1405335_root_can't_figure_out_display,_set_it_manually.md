---
title: "root: can't figure out display, set it manually"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by TheUnaligned on 2010-02-12
So I just installed Ubuntu 64-bit on my desktop (triple boot w/ XP and 7, each OS on its own HD). I am having trouble getting it to boot to desktop. When I turn it on, it takes me to the shell w/ a command line. After I login and type 'root', it tells me the follwing:

"root: can't figure out DISPLAY, set it manually"

Now, I assume this is because there is no video driver (I know, I'm brilliant) the question I have is what do I do next? My video card is nVidia GT275.

Any help is appreciated.

EDIT: I have tried starting xwindows, to no avail.

[B]Commands attempted // result
[/B]
sudo dpkg-reconfigure xserver-xorg // nothing
sudo apt-get install ubuntu-desktop // nothing
startx // 'Failed to load module "nvidia" (module does not exist, 0)' *AND *'No drivers available' *AND *'Fatal server error: no screens found'

---

### Post by Scunizi on 2010-02-12
How about doing a full system upgrade first.. "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade" .. dist-upgrade will not take you to the next release but will upgrade packages to the newest available version if available.. then try starting the graphics again after a restart.  Another way to start gdm is "sudo service gdm start" or sudo /etc/init.d/gdm start... although in 9.10 the first method is more typical.

---

### Post by TheUnaligned on 2010-02-12
Ok, working through that. As a side note, I tried installing the driver by sudo apt-get install nvidia-glx-185 nvidia-kernel-common and it looks as if I've made some progress, it tries to start up and I get the Ubuntu logo, but the screen then goes blank... grr.

Why does this have to be so complicated? :)

---

### Post by Somnus07 on 2010-05-09
Um I was getting this error message when I was trying to run root (as in CERN's ROOT). And got it working by setting:
export DISPLAY=localhost:0.0
before running root.

---

### Post by Scunizi on 2010-05-09
I just realized.. you don't log into an ubuntu system with "root" .. or another way of putting it is you don't "su" to become root until "exit".  In ubuntu you use sudo before a command that needs root privileges.  Also your card might be a newer one (not familure with that model of nvidia).. If it's fairly new you might need to install the driver available direct from nvidia.. the 185 driver might not support your card.

---

### Post by kaiten65 on 2010-12-27
you just have to install gdm. run the install command and select/input gdm as package and your display should be configured

---

