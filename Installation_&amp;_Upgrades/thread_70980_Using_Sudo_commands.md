---
title: "Using Sudo commands"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by Brandon14u2 on 2005-10-01
Anytime I try to use a sudo command that I get off the internet, nothing happens.  In particular I'm trying to install Java Runtime.  I follow the directions and all that happens is that I get a black pop-up for a split second and then nothing. Sometimes I will see scrolling text and then nothing.   When I start Synaptic I get the following error which I thought may be connected, here it is.
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
Sorry if the above has no bearing on the problem.  Any help would be appreciated.  One other thing.  When I boot ubuntu, my keyboard locks up and I have to disconnect it and plug it back in to get it to work.  Thanks for any help.

---

### Post by aysiu on 2005-10-01
sudo's for the terminal.
Synaptic should just prompt you for a password.
The unofficial backports mirrors are down. I don't know where the official ones are, though.

Edit: Read [this thread](http://ubuntuforums.org/showthread.php?t=69681) for more info.

---

