---
title: "Dpkg Problems"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by Captiva on 2007-06-19
I believe I know the cause for this problem, I was trying to install Grapevine and got lost along the way.  Now I can't do anything with Synaptic programmes, them telling me to type "dpkg --console -a" into the Terminal. But when I do that, I need superuser privileges. Last I checked I am the only user on this PC and should be able to do anything.

Can anyone tell me how to fix this problem? I really want to avoid having to uninstall and reinstall, seeing how my primary reason in doing all this is to be able to put music on my Creative Zen V Plus. The only method I've seen including Amarok, which I need to install.

---

### Post by ArconWan on 2007-06-19
Technically, there is always another user on all Linux systems called root, which is the all-mighty superuser (though on secure Linux it is much weaker, but that's another story).  Your "only user" can, however, temporarily gain superuser privalages using the 'sudo' command.  You just have to call sudo followed by whatever you were going to do (same line), then enter you password if it asks.  For example, if you typed "sudo dpkg --console -a" then it should do what you want.

Ubuntu is the only Linux distro I've used that uses sudo, but it seems to work most of the time.

---

