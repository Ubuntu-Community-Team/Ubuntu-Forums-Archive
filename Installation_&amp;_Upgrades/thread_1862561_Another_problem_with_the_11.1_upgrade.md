---
title: "Another problem with the 11.1 upgrade"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by mrw on 2011-10-16
After the upgrade (there were some errors) I am only able to log into the command prompt - no GUI.
I have a NVIDIA card and tried
apt-get -f install nvidia-current
and among other errors received "Unmet dependencies. Try apt-get -f install with no packages.

I tried sudo apt-get -f install and got the following errors:

Failed to fetch [http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/) ----. Something wicked happened resovling 'us.archive.ubuntu.com:http' (-5 - No address associated iwth hostname).

I think if I had a 'proper' Xconfig.conf file I might get the display back.

Is there a way to reinstall the upgrade?
I tried to fool the system by changing the version number in the lsb-release file but that didn't work.
I have a live cd and can boot from that but there's no way to just do an upgrade.
I'm prepared to do a clean install but need to make sure by dual boot with windows 7 doesn't get disrupted.

Any ideas about fixing the damaged upgrade?

---

### Post by mrw on 2011-10-16
In my last post I meant Xorg.conf not Xconfig.conf,

---

