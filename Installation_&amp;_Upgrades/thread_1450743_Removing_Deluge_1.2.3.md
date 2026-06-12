---
title: "Removing Deluge 1.2.3"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by munishvit on 2010-04-09
Hi,

In order to upgrade Deluge to latest version, I removed its 1.1.9 version and somehow installed 1.2.3 on Ubuntu 9.10. 
Now when I start it I get connection error. So, I am trying to remove it, but in vain. 
I tried following commands:

sudo apt-get remove deluge
sudo apt-get --purge remove deluge
sudo aptitude purge deluge
sudo dpkg --remove --force-remove-reinstreq deluge

But, it's icon is still there in applications, though doesn't start d application if I click it and the command "deluge --version" gives "1.2.3".

Any help will be greatly appreciated. Thanks.

---

### Post by Cas07 on 2010-04-10
I do not see how you managed to install 1.2.3 on 9.10 from aptitude as it is not available in the official, PPA or GetDeb repos.
The only way would be from source so trying to uninstall with apt-get will not work. 

The Deluge website has details on removing the installed files: [http://dev.deluge-torrent.org/wiki/Installing/Source#RemovingFromSystem](http://dev.deluge-torrent.org/wiki/Installing/Source#RemovingFromSystem)

I would suggest installing Deluge 1.2.2 from the Deluge-team PPA [here]("https://launchpad.net/~deluge-team/+archive/ppa") as there is no difference between 1.2.2 and 1.2.3 with regards to Karmic.

---

### Post by munishvit on 2010-04-11
Thanks for the reply Caos. 
I removed all the files that I could find by typing "deluge" in "Search for files...". Then I installed it using "Ubuntu Software Center". This version 1.1.9 is now working fine. 
I tried the PPA you suggested for 1.2.2, but then sudo apt-get update was failing. 
Anyway thanks for the help.

---

### Post by Cas07 on 2010-04-12
There was a new release of 1.2.3 for karmic yesterday that may have caused the ppa to not update until it was ready. 

I would really recommend upgrading as the new version is actually quite different underneath. A lot of users are running latest Deluge on Karmic without any issue, all installed from PPA.

You can always visit the support forums [http://forum.deluge-torrent.org/index.php](http://forum.deluge-torrent.org/index.php) where we can give help if needed.

---

