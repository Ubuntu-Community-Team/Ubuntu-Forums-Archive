---
title: "Lirc installation failed, no package configuration running"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by ExpressTrain on 2008-12-01
I"m running Hardy Heron, and I was following the instructions to install Lirc from the Ubuntu documentation here: [https://help.ubuntu.com/community/InstallLirc/Hardy]("https://help.ubuntu.com/community/InstallLirc/Hardy").  After installing via the Synaptic package manager, the instructions say I should expect to see some kind of configuration screen.  I never saw it, so I wonder if something failed to install.  I tried marking Lirc for re-install via Synaptic, and still no configuration screen.  

Other information that may (or may not) be helpful:  There is a lirc in /etc/init.d but when I try to run ```
sudo /etc/init.d/lirc start
``` or ```
sudo /etc/init.d/lirc restart
``` nothing happens, and there is no lircd running when I do a ps -ef | grep lircd.  I also looked in /etc/lirc and there are some lirc configuration files (like lircd.conf) which I assume were supposed to get written by the package configuration tool, but they look pretty empty to me.

Should I have seen the package configuration screen?  And if so, could this be the root cause of why Lirc is not running?

One last note, in Synaptic, I thought about completely removing Lirc and re-installing it, but when I marked it for removal, Synaptic looks like it wants to remove a bunch of other packages too, like Mythtv, which is what I have been struggling to get working for a few months now.  So I basically chickened out of removing Lirc.  Are my fears about having to start over with Mythtv unfounded?

---

