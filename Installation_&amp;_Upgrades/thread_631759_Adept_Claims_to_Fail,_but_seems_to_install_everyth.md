---
title: "Adept Claims to Fail, but seems to install everything fine"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by panda726 on 2007-12-04
Not exactly a problem, perhaps a bug.  When I install anything from either Adept Installer or Package Manager, it downloads my program fine, then goes to install it, and partway through it pops up an error message "There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages."  When  I close this, it says "Installation Complete", and the programs work perfectly (as far as I have tried any of them)

I am running Gutsy, upgraded from Feisty by formatting / with /home on a separate partition which I left alone and mounted as /home in my new install.  I used the live CD for the install.  (I know I perhaps could have done it differently, but I do like clean installs as well (I do know that this is much more important with windows than linux).)

Tor

---

### Post by BryanFRitt on 2007-12-10
I had the same problem, or something similar.
Try looking at the details for the last install, there might be programs that didn't install from a previous install.
Try installing what ever it said didn't install from a console.  
sudo apt-get install packagesListThatDidNotInstall
They might require some user feedback to finish installation.

---

