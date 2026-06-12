---
title: "Upgrading 14.04 LTS to 16.04 LTS problems with insserv"
date: 2017-02-27
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2017-02-27
I am getting ready to upgrade some of my production servers from 14.04 to 16.04 I ran the upgrade on one sample and was able to get it to work but encountered problems with insserv but was able to work through them without really understanding the problem. 

I ran the upgrade on a second machine and it is badly broken.  I have run

dpkg --configure -a
apt-get -f install
dpkg --configure -a --force depends 
apt-get autoremove
apt-get clean

56 packages remain unconfigured.

even trying to configure one package generates a lot of warnings and some errors. Configuring each package with dpkg results in dependance errors from other packages, however when I get to the package that will attempt to configure I get a lot of warnings from insserv about the scripts and an error usplash and bittorrent

There is a loop involving service usplash and bittorrent
    loop involving service usplash is at depth 1
    loop involving service bittorrent is at depth 2

Thanks for any tips.

---

