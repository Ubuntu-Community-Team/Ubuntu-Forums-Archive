---
title: "python defective after dist upgrade - reinstall?"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by martux on 2012-04-15
I carried out two upgrades from 10.04 to 11.04. Unfortunately something with the python setup went wrong. All python programs like ipython just return "Aborted". Starting the python command line works but e.g. "import numpy" again quits with the same message.
No clue what's going on. Any suggestions about how I can track down the problem? Is there a way to reinstall python?

Cheers, M

---

### Post by oldfred on 2012-04-17
Can you boot or at least boot to command line? If so just run this.

apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

sudo apt-get install python

If you cannot boot then you will have to chroot into your install.

---

